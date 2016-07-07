<a name="sec5"></a>

## 5. Assertion Strength

Assertion とは, Authenticated Subscriber に関する一連の Claim および Statement を含んだものである.
Assertion はその利用方法の特徴や保護方法などの複数の軸でカテゴライズされる.

<!-- An assertion contains a set of claims or statements about an authenticated subscriber. Assertions can be categorized along multiple orthogonal dimensions, including the characteristics of using the assertion or the protections on the assertion itself. -->

Assertion に含まれるコアとなるべき (SHOULD) Claim は以下の通りである (が, これに限らない):

<!-- The core set of claims inside an assertion SHOULD include (but is not limited to): -->

- Issuer: Assertion 発行主体 (CSP) の識別子.
- Subject: 当該 Assertion が指し示す主体 (Subscriber) の識別子, 通常は Issuer (CSP) の管理する Namespace 内で有効である.
- Audience: Assertion を受け取る主体 (RP) の識別子.
- Issuance: Assertion が CSP に発行された日時を示すタイムスタンプ.
- Expiration: Assertion の有効期限を示すタイムスタンプ. 有効期限が切れたものは RP に valid な Assertion として受け入れられるべきでない (SHALL).
- Authentication Time: CSP が Primary Authentication Event を通じて Subscriber を認証した日時を示すタイムスタンプ.
- Identifier: 当該 Assertion 自身を識別するランダムでユニークな値. 攻撃者が不正な Assertion を生成して validity check をパスするのを防ぐ目的で利用される.

<!--
 - Issuer: an identifier for the party that issued the assertion (the CSP)
 - Subject: an identifier for the party that the assertion is about (the subscriber), usually within the namespace control of the issuer (the CSP)
 - Audience: an identifier for the party intended to consume the assertion (the RP)
 - Issuance: a timestamp indicating when the assertion was issued by the CSP
 - Expiration: a timestamp indicating when the assertion expires and SHALL no longer be accepted as valid by the RP
 - Authentication Time: a timestamp indicating when the CSP last verified the presence of the subscriber at the CSP through a primary authentication event
 - Identifier: a random value uniquely identifying this assertion, used to prevent attackers from manufacturing malicious assertions which would pass other validity checks
-->

これらのコアとなる Claim の中でも, 特に Issuance と Expiration Claim は, その Assertion が指し示す Authentication Event 自体に関連し, Subscriber に紐付いたその他の付加的な Identity Attributre には関連しない.
Subscriber Attribute は, Assertion 自体の Expiration や Invalidation とは独立して Expire したり Invalidate されたりしうる (MAY).

<!-- These core claims, particularly the issuance and expiration claims, apply to the assertion about the authentication event itself, and not to any additional identity attributes associated with the subscriber, even when those claims are included within the assertion. A subscriber's attributes MAY expire or be otherwise invalidated independently of the expiration or invalidation of the assertion. -->

Assertion は上記以外の Identity Attributes を含んでもよい (MAY) が, 可能な限り Authentication Transaction の処理に必要な情報のみを含めることを推奨する (SHOULD).
RP は, その他の Identity Attributes を, Assertion と同時に発行された Authorization Credential を用いて別 Trancation で CSP から取得できる (MAY).

<!-- Assertions MAY include other additional identity attributes, but where possible the information contained in the assertion SHOULD be limited to the information required to process the authentication transaction. The RP MAY fetch additional identity attributes from the CSP in a separate transaction using an authorization credential issued along side the assertion. -->

詳細は Federation Protocol ごとに異なるが, Assertion は RP での個々のログインイベントのみを表現するべきである (SHOULD).
ひとたび RP が Assertion を受け取って処理を完了すれば, その後は [session management](sp800-63b.html#sec7) の段階に移り, 当該 Assertion を直接利用することはない.

<!-- Although details vary based on the exact federation protocol in use, an assertion SHOULD be used only to represent a single log-in event at the RP. After the RP consumes the assertion, [session management](sp800-63b.html#sec7) at the RP comes into play and the assertion is no longer used directly. -->

### 5.1. Assertion possession category

Assertion は, Assertion を所有している主体が Assertion の Subject となるか, Assertion とは別に Subject であることを示す証拠が必要かという, 所有者の表現方法で分類できる.

<!-- An assertion can be classified based on whether possession of the assertion itself is sufficient for representing  the subject of the assertion, or if additional proof is necessary along side the assertion. -->

#### 5.1.1. Holder-of-Key Assertions

Holder-of-Key Assertion は, Subscriber の持つ共通鍵ないしは (秘密鍵とペアとなる) 公開鍵の参照を含む.
RP は Subscriber に対して, Assertion 自体とは別に, 当該鍵を所有している証拠を示すよう要求できる.

<!-- A holder-of-key assertion contains a reference to a symmetric key or a public key (corresponding to a private key) possessed by and representing the subscriber. The RP may require the subscriber to prove possession of the key that is referenced in the assertion in parallel with presentation of the assertion itself. -->

Subscriber が鍵を所有している証拠を提示できれば, Subscriber は当該 Assertion の正式な Subject であることをある程度の確からしさを持って証明できる.
攻撃者が Subscriber あてに発行された Holder-of-Key Assertion を盗んだとしても, 攻撃者は Subscriber の鍵も同時に盗まなければならず, 盗んだ Assertion を利用するのは困難となる.

<!-- In proving possession of the subscriber’s secret, the subscriber also proves with a certain degree of assurance that they are the rightful subject of the assertion. It is more difficult for an attacker to use a stolen holder-of-key assertion issued to a subscriber, since the attacker would need to steal the referenced key material as well. -->

鍵の参照は Assertion の Issuer がその他の Claim 同様に Assert するものであるから, その参照もまた当該 Assertion に含まれる他の Claim と同じレベルの信頼度を持った情報として扱うべきである (SHALL).

<!-- Note that the reference to the key material in question is asserted by the issuer of the assertion as are any other claims therein, and reference to a given key SHALL be trusted at the same level as all other claims within the assertion itself. -->

#### 5.1.2. Bearer Assertions

Bearer Assertion は, Bearer (持参人) 自身が誰であれ, Bearer 自身の Identity の証拠としてその Assertion を提示することができる.
その他の鍵などへのリファレンスは不要である.
もし攻撃者が Subscriber を示す正規の Assertion をキャプチャまたは生成できてしまえば, 攻撃者はその Assertion を RP に提示するだけで Subscriber になりすますことができる.

<!-- A bearer assertion can be presented by any party as proof of the bearer's identity, without reference to external materials. If an attacker is able to capture or manufacture a valid assertion representing a subscriber, and that attacker is able to successfully present that assertion to the RP, then the attacker will be able to impersonate the subscriber at that RP. -->

ただし Bearer Assertion を取得することだけが Subscriber になりすます条件であることは稀であり, 後述の Indirect Federation Model (Section 6.1) のように, 実際には Assertion に RP の識別情報を含んだり Assertion Injection を防いだりといった, RP への不正なアクセスを防ぐ追加の防御策が施されているものである (MAY)

<!-- Note that mere possession of a bearer assertion is not always enough to impersonate a subscriber. For example, if an assertion is presented in the indirect federation model (Section 6.1), additional controls MAY be placed on the transaction (such as identification of the RP and assertion injection protections) that help to further protect the RP from fraudulent activity. -->

### 5.2. Assertion protection category

上記の Assertion の所有方式や Section 4 で触れた Assertion 取得に用いる Federation Model とは別に, Assertion は偽造や他 RP に対する再利用を防ぐ何らかの保護策を内包する必要がある.

<!-- Regardless of the possession mechanism (discussed above) or the federation model used to obtain them (described in section 4), assertions need to include an appropriate set of protections to the assertion data itself to prevent attackers from manufacturing valid assertions or re-using captured assertions at disparate RPs. -->

#### 5.2.1. Shared Secret

Assertion は偽造防止の目的で十分なエントロピーを持つべきである (SHALL).
この目的には 128-bit ランダム共有鍵か同等の非対称鍵を利用すべきである (SHALL).
同様に nonce, timestamp, assertion identifier, それらの組み合わせやその他のテクニックを使ってもこの目的を達成できる (MAY).

<!-- Assertions SHALL contain sufficient entropy to prevent an attacker from manufacturing a valid assertion and using it with a target RP. A 128-bit random symmetric key or equivalent strength asymmetric key SHALL be used for this purpose. Assertions MAY accomplish this by use of an embedded nonce, timestamp, assertion identifier, or a combination of these or other techniques. -->

その他の暗号論的保護策がない場合, こういったランダム性を CSP と RP の間で Assertion をユニークに識別するための共有鍵として扱うべきであろう (SHALL).

<!-- In the absence of additional cryptographic protections, this source of randomness SHALL function as a shared secret between the CSP and the RP to uniquely identify the assertion in question. -->

#### 5.2.2. Signed Assertion

CSP は Assertion に暗号論的に署名することもできる (MAY).
RP は CSP の鍵を用いて各 Assertion の署名を検証すべきである (SHALL).
この署名は, Issuer, Audience, Subject, Expiration, その他の各種識別子等, Assertion に含まれる重要なフィールド全体に対してなされるべきである (SHALL).

<!-- Assertions MAY be cryptographically signed by the CSP, and the RP SHALL validate the signature of each such assertion based on the CSP's key. This signature SHALL cover all vital fields of the assertion, including its issuer, audience, subject, expiration, and any unique identifiers. -->

CSP が公開鍵を公開する鍵ペアによって署名を行うこともでき (MAY), その場合 RP は公開鍵を (CSP がホストする HTTPS URL などから) 動的かつセキュアに取得することができる (MAY).
鍵はそれ以外の何らかの方法で RP に提供されてもよい (MAY).

<!-- The signature MAY be asymmetric based on the published public key of the CSP. In such cases, the RP MAY fetch this public key in a secure fashion at runtime (such as through an HTTPS URL hosted by the CSP), or the key MAY be provisioned out of band at the RP. -->

CSP と RP の間で何らかの方法で共有された共通鍵による署名を用いることもできる (MAY).
その場合 CSP は RP ごとに異なる鍵を用いるべきである (SHALL).

<!-- The signature MAY be symmetric based on a key shared out of band between the CSP and the RP. In such circumstances, the CSP SHALL use a different shared key for each RP. -->

署名には Approved Signing Method のいずれかを利用すべきである (SHALL).

<!-- All signatures SHALL use approved signing methods. -->

#### 5.2.3. Encrypted Assertion

意図された Audience のみが復号できる形で Assertion を暗号化することもできる (MAY).
CSP は RP の公開鍵で Assertion を暗号化すべきである (SHALL).
その場合 CSP は RP の公開鍵を (RP がホストする HTTPS URL などから) 動的かつセキュアに取得することができる (MAY).
鍵はそれ以外の何らかの方法で (RP の登録時などに) CSP に提供されてもよい (MAY).

<!-- Assertions MAY be encrypted in such a fashion as to allow only the intended audience to decrypt the claims therein. The CSP SHALL encrypt the payload of the assertion using the RP's public key. The CSP MAY fetch this public key in a secure fashion at runtime (such as through an HTTPS URL hosted by the RP), or the key MAY be provisioned out of band at the CSP (during registration of the RP). -->

暗号化には Approved Encryption Method のいずれかを利用すべきである (SHALL).

<!-- All encrypted objects SHALL use approved encryption methods. -->

#### 5.2.4. Audience Restriction

すべての Assertion は Audience Restriction を施し, RP が当該 Assertion の発行先が自分自身であるかどうかを検知できるようにすべきである (SHOULD).
Audience が含まれている場合, RP は Assertion の Audience をチェックし, ある RP に対して発行された Assertion がその他の RP に対して利用されることを防止しべきである (SHALL).

<!-- All assertions SHOULD use audience restriction techniques to allow an RP to recognize whether or not it is the intended target of an issued assertion. All RPs SHALL check the audience of an assertion, if provided, to prevent the injection and replay of an assertion generated for one RP at another RP. -->

#### 5.2.5. Pseudonymous Identifiers

CSP 上の Subscriber アカウントが共通識別子を通じて複数の RP 間でリンクされることを防ぐには, Subject Identifier として仮名識別子を利用するべきである (SHALL).
CSP は各 RP ごとに異なる仮名識別子を生成すべきである (SHALL).

<!-- To prevent the subscriber's account at the CSP from being linked through one or more RPs through use of a common identifier, pseudonymous subject identifiers SHALL be used within the assertions generated by the CSP for the RP. The CSP SHALL generate a different identifier for each RP. -->

