<a name="sec8"></a>

## 8. Security

*This section is non-normative.*

CSP, RP, Subscriber および代表的な Assertion Transaction の登場人物ではない主体も含めて, いかなる主体も悪意を持ったり不正アクセスの被害にあう可能性を否定できない.
攻撃者は, Assertion を偽造したり置換したりすることで, RP が提供するリソースやサービスへのより多くのアクセス権限を取得しようと試みるかもしれない.
同様に攻撃者は, Assertion や Assertion の参照を詐取したり偽造したりすることで, Subscriber になりすましたり, 本来は権限を持たないはずのデータやサービスにアクセスしようと試みるかもしれない.
さらに, 2つ以上の主体が共謀し, その他の主体を攻撃することも考えられる.
攻撃者は, Assertion データの Integrity や Confidentiality を損なわせることで, Assertion Protocol 自体を転覆させるかもしれない.
こういった一連の脅威に対しては, たとえ認可済みであったとしても, 自身が持つ権限を超えたアクセスを試みる主体は攻撃者とみなされる.
本セクションでは Assertion 伝送トランザクションにおける一般的攻撃パターンについてまとめる.

<!-- CSPs, RPs, subscribers, and parties outside of a typical assertions transaction may be malicious or become compromised. An attacker might have an interest in modifying or replacing an assertion to obtain a greater level of access to a resource or service provided by an
RP. They might be interested in obtaining or modifying
assertions and assertion references to impersonate a subscriber or
access unauthorized data or services. Furthermore, it is possible that
two or more entities may be colluding to attack another party. An
attacker may attempt to subvert assertion protocols by directly
compromising the integrity or confidentiality of the assertion data. For
the purpose of these types of threats, authorized parties who attempt to
exceed their privileges may be considered attackers. This section lists some common attacks against assertion transmission transactions. -->


-   *Assertion manufacture/modification* - 攻撃者は Assertion を偽造したり既存の Assertion のコンテンツ (Authentication Statement や Attribute Statement 等) を改ざんしたりして, RP が Subscriber に不正なアクセスを許すように仕向けることがある.
    例えば, 攻撃者が Assertion の有効期間を延長してその Assertion を利用し続けたり, Subscriber が Assertion を改ざんして Subscriber には本来アクセスできないはずの情報にアクセスしたりするといったことが考えうる.
<!-- -   *Assertion manufacture/modification* – An attacker generates a
    forged assertion or modifies the content of an existing assertion (such as the
    authentication or attribute statements),
    causing the RP to grant inappropriate access to the subscriber. For
    example, an attacker may modify the assertion to extend the validity
    period and keep using an assertion; or a subscriber may modify the assertion to have access to
    information that they should not be able to view. -->

-   *Assertion disclosure* - Assertion には Authentication Statement と Attribute Statement を含まれうるが, それらの Statement は Subscriber に関するセンシティブな情報を含み得る.
    Assertion に含まれるコンテンツが漏洩すると, Subscriber がその他の攻撃に狙われることにつながる.
<!-- -   *Assertion disclosure* – Assertions may contain authentication and
    attribute statements that include sensitive subscriber information.
    Disclosure of the assertion contents can make the subscriber
    vulnerable to other types of attacks. -->

-   *Assertion repudiation by the CSP* - Assertion は適切なメカニズム無しでは CSP から否認されうる.
    CSP が Assertion に電子署名を行っていない場合などは, CSP が当該 Assertion を自身のサービスを通じて発行したものではないと主張することがある.
<!-- -   *Assertion repudiation by the CSP* – An assertion may be
    repudiated by a CSP if the proper mechanisms are not in place.
    For example, if a CSP does not digitally sign an assertion, the
    CSP can claim that it was not generated through the services of
    the CSP. -->

-   *Assertion repudiation by the subscriber* - 不正アクセスされたり悪意を持った Subscriber は Assertion を非正規な主体に対して発行することができるため, Subscriber は Bearer Assertion で認証された RP とのあらゆるトランザクションを否認する可能性がある.
<!-- -   *Assertion repudiation by the subscriber* – Since it is possible for
    a compromised or malicious subscriber to issue assertions to the
    wrong party, a subscriber can repudiate any transaction with the RP
    that was authenticated using only a bearer assertion. -->

-   *Assertion redirect* - 攻撃者はある RP に対して発行された Assertion を異なる RP に対して利用して, アクセスを試みることがある.
<!-- -   *Assertion redirect* – An attacker uses the assertion generated for
    one RP to obtain access to a second RP. -->

-   *Assertion reuse* - 攻撃者はすでに発行相手となる RP との間で一度利用された Assertion を, 再度利用しようとすることがある.
<!-- -   *Assertion reuse* – An attacker attempts to use an assertion that
    has already been used once with the intended RP. -->

場合によっては Subscriber は何らかの鍵情報を発行され, それを使って RP に認証することもある.
このような鍵情報は Subscriber と Subscriber になりすまそうとする攻撃者を区別するために利用できる.
Holder-of-Key Assertion を使う場合は, この鍵は Assertion Protocol を開始する前に事前に CSP との間で確立されていることもある.
また CSP がテンポラリな鍵を生成し, 認証済の Subscriber にその鍵を送付することもある.
テンポラリな鍵を RP への認証に用いる場合は, そういった鍵は Secondary Authenticator と呼ばれる.
Direct Mode での Assertion, Kerberos の Session Key, Indirect Mode での Assertion の参照, 認証 Cookie なども, Secondary Authenticator の一種である.
Secondary Authenticator に対する脅威としては, 以下のようなものがあげられる.

<!-- In
some cases, the subscriber is
issued some secret information so that they can be recognized by the RP. The knowledge of this information distinguishes the
subscriber from attackers who wish to impersonate the them. In the
case of holder-of-key assertions, this secret could already have been
established with the CSP prior to the initiation of the assertion
protocol. In other cases, the CSP will generate a temporary secret
and transmit it to the authenticated subscriber for this purpose. When this secret is used to authenticate to the RP, this temporary secret will be referred to as a secondary
authenticator. Secondary authenticators include assertions in the direct
model, session keys in Kerberos, assertion references in the indirect
model, and cookies used for authentication. The threats to the secondary
authenticator are as follows: -->

-   *Secondary authenticator manufacture* - 攻撃者は有効な Secondary Authenticator を生成して Subscriber になりすまそうとする.
<!-- -   *Secondary authenticator manufacture* – An attacker may attempt to
    generate a valid secondary authenticator and use it to impersonate
    a subscriber. -->

-   *Secondary authenticator capture* - 攻撃者は, Session ハイジャック攻撃等により, Primary Authentication 完了後に CSP から Subscriber に伝送される Secondary Authenticator をキャプチャーしようとすることもある.
    また Man-in-the-Middle 等により Subscriber から RP に送られる Secondary Authenticator を搾取することも考えらえる.
    Indirect Mode のように, RP が Secondary Authenticator を CSP に送ってその正当性をチェックしたり Secondary Authenticator に紐づく Assertion データを取得したりする必要がある場合, 攻撃者は CSP と RP の間の通信プロトコルに対する攻撃等により Secondary Authenticator をキャプチャーすることもありうる.
    このようなケースでは, Secondary Authenticator は Subscriber になりすますために利用されるであろう.
<!-- -   *Secondary authenticator capture* – An attacker may use a session
    hijacking attack to capture the secondary authenticator when the
    CSP transmits it to the subscriber after the primary
    authentication step, or the attacker may use a man-in-the-middle
    attack to obtain the secondary authenticator as it is being used by
    the subscriber to authenticate to the RP. If, as in the indirect
    model, the RP needs to send the secondary authenticator back to the
    CSP in order to check its validity or obtain the corresponding
    assertion data, an attacker may similarly subvert the communication
    protocol between the CSP and the RP to capture a
    secondary authenticator. In any of the above scenarios, the
    secondary authenticator can be used to impersonate the subscriber. -->

最後に, Subscriber が RP に対して認証を行うためには, RP への認証に用いる鍵と Subscriber を示す Assertion との紐づけを強固にする必要がある.

<!-- Finally, in order for the subscriber’s authentication to the RP to be
useful, the binding between the secret used to authenticate to the RP
and the assertion data referring to the subscriber needs to be strong. -->

-   *Assertion substitution* – Subscriber は, CSP と RP の間のコミュニケーションチャネルに攻撃を仕掛けることで, より権限の強い Subscriber になりすますかもしれない.
    例えば, メッセージの順序を変更して, 送られてきた Secondary Authenticator がより権限を持つ Subscriber を示す Assertion と紐付いているかのように見せかけるなどの例が考えられる.
<!-- -   *Assertion substitution* – A subscriber may attempt to impersonate a
    more privileged subscriber by subverting the communication channel
    between the CSP and RP, for example by reordering the messages,
    to convince the RP that their secondary authenticator
    corresponds to assertion data sent on behalf of the more
    privileged subscriber. -->


### 8.1. Threat Mitigation Strategies

上記のそれぞれの脅威に対する防御策を以下に示す.

<!-- Mitigation techniques are described below for each of the threats
described in the last subsection. -->

-   *Assertion manufacture/modification*: この脅威を防ぐためには, 以下の対策を行うこと.
<!-- -   *Assertion manufacture/modification*: To mitigate this threat,
    the following mechanisms are used: -->

    1.  CSP は Assertion に対して電子署名を行う. RP は電子署名を検証し, 当該 Assertion が正規の CSP から発行されていることを確認する.
    <!-- 1.  The assertion is digitally signed by the CSP. The RP
    checks the digital signature to verify that it was issued by a
    legitimate CSP. -->

    2.  Assertion を TLS 等の保護されたセッションを使って伝送する. 悪意ある攻撃から Assertion の Integrity を保護するために, CSP を認証すること.
    <!-- 2.  The assertion is sent over a protected session such as TLS. In
    order to protect the integrity of assertions from malicious attack,
    the CSP is authenticated. -->

    3. Assertion に推測不可能な識別子を含める.
    <!-- 3. The assertion contains a non-guessable random identifier. -->

-   *Assertion disclosure* – この脅威を防ぐためには, 以下のいずれかの対策を行うこと.
<!-- -   *Assertion disclosure* – To mitigate this threat, one of the
    following mechanisms are used: -->

    1.  Assertion を保護されたセッションを通じて認証された RP に伝送する.
    保護されたセッションを利用して Assertion を漏洩・偽造・改ざんのすべてから保護するには, RP, CSP 双方が検証される必要があることに注意.
    <!-- 1.  The assertion is sent over a protected session to an
    authenticated RP. Note that, in order to protect assertions against
    both disclosure and manufacture/modification using a protected
    session, both the RP and the CSP need to be validated. -->

    2.  CSP は Assertion に電子署名をしたのち特定の RP に対して暗号化する.
    この方法は双方向に認証されたセッションを利用した場合と等価である.
    したがって, Assertion を漏洩・偽造・改ざんから保護するための要件を一般化すると, 双方向に認証された保護セッションを利用するか, CSP と RP の間でそれに等しい対策を行うこと, となろう.
    <!-- 2.  Assertions are signed by the CSP and encrypted for
    a specific RP.  It should be
    noted that this provides all the same guarantees as a mutually
    authenticated protected session, and may therefore be
    considered equivalent. The general requirement for protecting
    against both assertion disclosure and assertion
    manufacture/modification may therefore be described as a mutually
    authenticated protected session or equivalent between the CSP
    and the RP. -->

-   *Assertion repudiation by the CSP* – この脅威を防ぐためには, CSP が Assertion に電子署名を行い, 署名に使う鍵として否認防止が可能なものを利用する必要がある.
    RP は署名を検証して当該 Assertion が正規の CSP から発行されたものであるかをチェックすること.
<!-- -   *Assertion repudiation by the CSP* – To mitigate this threat,
    the assertion is digitally signed by the CSP using a key
    that supports non-repudiation. The RP checks the digital
    signature to verify that it was issued by a legitimate CSP. -->

-   *Assertion repudiation by the subscriber* – この脅威を防ぐためには, CSP が Bearer Assertion ではなく Holder-of-Key Assertion を発行する必要がある.
    Holder-of-Key Assertion を利用する際は, Subscriber が Assertion に紐付いた鍵を保有している証拠を RP に提示することになる.
    そのため全主体が, RP に Assertion を提示したのが正規の Subscriber であり, 悪意ある CSP が Subscriber になりすまそうとしているのではないことを確認できる.
<!-- -   *Assertion repudiation by the subscriber* – To mitigate this threat,
    the CSP issues holder-of-key assertions, rather than bearer assertions.
    The subscriber can then prove possession of the asserted key to
    the RP. If the asserted key matches the subscriber’s presented key,
    it will be proof to all parties
    involved that it was the subscriber who authenticated to the RP
    rather than a compromised CSP impersonating the subscriber. -->

-   *Assertion redirect* – この脅威を防ぐためには, Assertion に発行先の RP の Identity を含める必要がある.
    RP は受け取った Assertion の受取人が自身であることを検証すること.
<!-- -   *Assertion redirect* – To mitigate this threat, the assertion
    includes the identity of the RP for which it was generated. The RP
    verifies that incoming assertions include its identity as the
    recipient of the assertion. -->

-   *Assertion reuse* – この脅威を防ぐためには, 以下の対策を行うこと.
<!-- -   *Assertion reuse* – To mitigate this threat, the following
    mechanisms are used: -->

    1. Assertion に Timestamp を含め, 有効期限を短くする.
    RP は Timestamp と有効期限をチェックして, 当該 Assertion がその時点で有効であることを確認する.
    <!-- 1.  The assertion includes a timestamp and has a short lifetime
    of validity. The RP checks the timestamp and lifetime values to
    ensure that the assertion is currently valid. -->

    2.  RP は (設定可能な) 一定期間受け取った Assertion をトラックし, その期間内に Assertion が再利用されていないことを確認する.
    <!-- 2.  The RP keeps track of assertions that were consumed within
    a (configurable) time window to ensure that an assertion is not
    used more than once within that time window. -->

-   *Secondary authenticator manufacture* – この脅威を防ぐためには, 以下のいずれかの対策を行うこと.
<!-- -   *Secondary authenticator manufacture* – To mitigate this threat, one
    of the following mechanisms is used: -->

    1.  Secondary Authenticator に十分なエントロピーを持たせ, CSP の乱数生成機への直接アクセス無しには正規の Secondary Authenticator を推測不可能にする.
    <!-- 1.  The secondary authenticator may contain sufficient entropy that an
    attacker without direct access to the CSP’s random number
    generator cannot guess the value of a valid secondary authenticator. -->

    2.  Secondary Authenticator にタイムリーな Assertion Data を含め, 一定期間のみ有効なものとする.
    この Assertion Data は CSP による署名や CSP と RP との間の共有鍵による Integrity 保護を行うこと.
    <!-- 2.  The secondary authenticator may contain timely assertion data that
    is signed by the CSP or integrity protected using a key shared
    between the CSP and the RP. -->

-   *Secondary authenticator capture* – この脅威を防ぐためには, Assertion Protocol で利用される Secondary Authenticator の有効期間全体を通じて, 適切な保護策が必要となる.
<!-- -   *Secondary authenticator capture* – To mitigate this threat,
    adequate protections are in place throughout the lifetime of
    any secondary authenticators used in the assertion protocol. -->

    1. CSP と Subscriber の間で Secondary Authenticator を伝送する際は, Subscriber の Primary Authentication 時に確立された保護セッションを通じて Secondary Authenticator を送信する.
    <!-- 1.  In order to protect the secondary authenticator while it is in
    transit between the CSP and the subscriber, the secondary
    authenticator is sent via a protected session established
    during the primary authentication of the subscriber. -->

    2. RP に送信される Secondary Authenticator をキャプチャから守るには, 盗聴や Man-in-the-Middle 攻撃から Secondary Authenticator を保護する何らかの認証プロトコルを利用する.
    <!-- 2.  In order to protect the secondary authenticator from capture as it
    is submitted to the RP, the secondary authenticator is used in
    an authentication protocol which protects against eavesdropping and
    man-in-the-middle attacks. -->

    3. Secondary Authenticator を再利用から守るには, Secondary Authenticator の有効期限を迎えるまで, 当該 Secondary Authenticator を保護されていないセッションを通じて伝送したり, 認証されていない主体に送信したりしてはならない.
    <!-- 3.  In order to protect the secondary authenticator after it has been
    used, it is never transmitted over an unprotected session or to
    an unauthenticated party while it is still valid. -->

-   *Assertion substitution* – この脅威を防ぐためには, 以下のいずれかの対策を行うこと.
<!-- -   *Assertion substitution* – To mitigate this threat, one of the
    following mechanisms is used: -->

    1. Assertion Request に対する Response に, リクエスト時に指定された Assertion 参照値や, RP が暗号論的に当該リクエストに紐づけた nonce を含める.
    <!-- 1.  Responses to assertion requests contain the value of the assertion reference used
    in the request or some other nonce that was cryptographically bound
    to the request by the RP. -->

    2. Assertion Request に対する Response を対応するリクエストと HTTP のメッセージ順通りに紐付けること.
    TLS などで Assertion と Request を保護すれば, 許可されていない悪意あるパケット順序入れかえを検知できる.
    <!-- 2.  Responses to assertion requests are bound to the corresponding
    requests by message order, as in HTTP, provided that assertions and
    requests are protected by a protocol such as TLS that can detect and
    disallow malicious reordering of packets. -->
