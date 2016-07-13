<a name="sec6"></a>

## 6. Assertion Presentation

Assertion は CSP から RP に対して *indifect* ないしは *direct* に提示される.
どちらのモデルにも利点と欠点があるが, いずれにせよ Assertion を正しく検証する必要があるのは同じである.
Section 4.1.4 にあるように, ある条件下では Federation を簡単にするため CSP と RP の間を Proxy した状態で Assertion をやりとりすることもある.

<!-- Assertions MAY be presented in either an *indirect* or *direct* manner from the CSP to the RP. Each model has its benefits and drawbacks, but both require the proper validation of the assertion. Assertions MAY also be proxied to facilitate federation between CSPs and RPs under specific circumstances, as discussed in section 4.1.4. -->

Subscriber の属性が RP に渡される前に, Subscriber による同意を得るべきである (SHALL).
もし利用するプロトコルが追加の属性のやりとりをサポートしている場合, Subscriber はそれらの属性についても RP に渡すか否かの選択肢を与えられるべきである (SHALL).
CSP はある RP に送信された Attribute Bundle を記憶し, 同じ RP へ当該 Attribute Bundle を再送信するような仕組みを導入してもよい (MAY).
CSP は RP から明示的に要求された属性のみを返すべきである (SHALL).
Assertion の提示方法は, Subscriber への明示と同意取得を誰が行うのが最適かという点に影響する.
したがって, CSP, RP および Broker は, 誰が明示と同意取得を行うかをあらかじめ取り決めておくべきである (SHALL).

<!-- Positive confirmation SHALL be obtained from the subscriber before any attributes about the subscriber are transmitted to any RP. If the protocol in use allows for optional attributes, the subscriber SHALL be given the option to decide whether transmit those attributes to the RP. A CSP MAY employ mechanisms to remember and re-transmit the exact attribute bundle to the same RP. The CSP SHALL transmit only those attributes that were explicitly requested by the RP. The manner of presentation may impact who is in the best position to provide notice and obtain confirmation from the subscriber.  Accordingly, the CSP, RP and any broker SHALL agree in advance on who will provide notice and obtain confirmation. -->

CSP は Subscriber に対して RP に渡された属性を確認できるようにすべきである (SHALL).
また (のぞき見などで) センシティブな情報が漏洩することを防ぐため, 必要に応じてマスキングなどを行うことも検討すること (SHALL).

<!-- The CSP SHALL enable the subscriber to view the attribute values to be transmitted. However, the CSP SHALL employ masking mechanisms, as necessary, to mitigate the risk of unauthorized exposure of sensitive information (e.g. shoulder surfing). -->

### 6.1. Indirect presentation

*indirect* モデルでは, Subscriber は Assertion の参照を渡され, HTTP Redirect などを通じてそれを RP に提示することになる.
Assertion の参照はそれ自身では Subscriber に関する情報は持たず, RP がその参照を CSP に提示して初めて Assertion が取得できる.
また RP が CSP に Assertion の参照を提示する際, 通常は RP の認証が行われる.

<!-- In the *indirect* model, the subscriber is given an assertion reference to present to the RP, such as an HTTP redirect. The assertion reference itself contains no information about the subscriber. The RP presents the assertion reference to the CSP, usually along with authentication of the RP itself, to fetch the assertion. -->

![Figure 1: Indirect presentation](sp800-63c/media/indirect.png)

**Figure 1: Indirect presentation**

このモデルでは, Assertion 自体は CSP から RP に直接渡されるため, (Subscriber 自身を含む) 3rd-party にインターセプトされたり改ざんされるリスクを最小化できる.
また RP が CSP に問い合わせる際に, Assertion には含まれない追加属性を要求することも可能となる.

<!-- In this model, the assertion itself is requested directly from the CSP to the RP, minimizing chances of interception and manipulation by a third party (including the subscriber themselves). This also allows the RP to query the CSP for additional attributes about the subscriber not included in the assertion itself. -->

Assertion 取得に Artifact の他に Proof of Key Possession 等の提示が必要とされていない限り, 当該 Assertion は依然として *Bearer* Assertion である.

<!-- The assertion is still considered a *bearer* assertion if the artifact required to fetch the Assertion does not require presentation of additional proof of key possession after the assertion has been fetched. -->

Indirect モードでは, ネットワークトランザクションがより多く必要となる一方, やり取りされる情報はそれを必要としている主体以外に渡されることはない.
RP が CSP から直接 Assertion を受け取るため, 攻撃箇所は限定される.

<!-- In the indirect method, there are more network transactions required, but the information is limited to the parties that need it. Since an RP is expecting to get an assertion only from the CSP directly, the attack surface is reduced. -->

Assertion に含まれる Claim は Issuer Verification, Signature Validation, Audience Restriction 等により検証されるべきである (SHALL).

<!-- Claims within the assertion SHALL be validated including issuer verification, signature validation, and audience restriction. -->

CSP から Subscriber, Subscriber から RP へと Assetion の参照を送信する際には, 認証され保護された Channel を利用すべきである (SHALL).
RP から CSP に Assertion の参照を送信する際, CSP から RP に Assertion を送信する際も, 認証され保護された Channel を利用すべきである (SHALL).

<!-- Conveyance of the assertion reference from the CSP to the subscriber as well as from the subscriber to the RP SHALL be made over an authenticated protected channel. Conveyance of the assertion reference from the RP to the CSP as well as the assertion from the CSP to the RP SHALL be made over an authenticated protected channel. -->

### 6.2. Direct Presentation

*direct* モードでは, CSP は認証成功後 Assertion を生成しそれを Subscriber に直接渡す.
Subscriber は渡された Assertion を利用して RP に自身を認証する.
これはしばしば Subscriber のブラウザの機能を用いて実現される.

<!-- In the *direct* model, the CSP creates an assertion and sends it directly to the subscriber after successful authentication. The assertion is used by the subscriber to authenticate to the RP. This is often handled by mechanisms within the subscriber’s browser.) -->

![Figure 2: Direct presentation](sp800-63c/media/direct.png)

**Figure 2: Direct presentation**

このモードでは, Assertion はユーザーからアクセス可能である.
これは Assertion に含まれるシステム情報などの漏洩につながる可能性もある.
Assertion は Subscriber からも見える状態であるから, Subscriber が当該 Assertion を異なる RP に対して再利用することも可能である.

<!-- In the direct method, an assertion is visible to the user, which could potentially cause leakage of system information included in the assertion. Since the assertion is visible to the subscriber, the direct method also allows the assertion to be replayed to other RPs by the subscriber. -->

RP は, Cross-Site Scripting やその他の攻撃への対策を行い, 偽造された Assertion や Capture された Assertion を使った Injection 攻撃を防ぐべきである (SHALL).

<!-- The RP SHALL protect itself against injection of manufactured or captured assertions by use of cross-site scripting protection or other accepted techniques. -->

Assertion は Issuer Verification, Signature Validation, Audience Restriction 等により検証されるべきである (SHALL).

<!-- The assertion SHALL be validated including issuer verification, signature validation, and audience restriction. -->

CSP から Subscriber, Subscriber から RP へと Assetion を送信する際には, 認証され保護された Channel を利用すべきである (SHALL).

<!-- Conveyance of the assertion from the CSP to the subscriber as well as from the subscriber to the RP SHALL be made over an authenticated protected channel. -->

### 6.3. Assertion proxying

実装によっては, CSP, RP, Subscriber の中間者となる Proxy が CSP から Assertion を受け取り, その Assertion を元に RP に対して新たな Assertion を生成することもある.
CSP から見れば, こういった Proxy は RP となる.
RP から見れば, こういった Proxy は CSP となる.
(Section 4.1.4 参照)

<!-- In some implementations, a proxy takes in an assertion from the CSP and creates a derived assertion when interacting directly with the RP, acting as an intermediary between the subscriber, the CSP, and the RP. From the perspective of the true CSP, the proxy is a single RP. From the perspective of the true RPs, the proxy is a single CSP. (See section 4.1.4.) -->

こういった Proxy の利用目的としては, 以下のようなものがあげられる.

<!-- There are several common reasons for such proxies: -->

- 複数のユーザー認証が必要な RP にアクセスするためのポータルサイト.
<!-- - Portals that provide users access to multiple RPs that require user authentication -->

- RP のアクセスコントロールポリシーを満たすために必要な Web Caching の手段. 特に Subscriber が TLS クライアント認証を利用している場合.
<!-- - Web caching mechanisms that are required to satisfy the RP’s access control policies, especially when client-authenticated TLS with the subscriber is used -->

- TLS を終端しトラフィックを監視・コントロールする必要のあるネットワークモニタリングやフィルタリングの手段.
<!-- - Network monitoring and/or filtering mechanisms that terminate TLS in order to inspect and manipulate the traffic -->

すべての情報のやりとりは, 認証され保護された Channel を通じて行うべきである (SHALL).

<!-- Conveyance of all information SHALL be made over authenticated protected channels. -->

### 6.4. Protecting Information

CSL と RP の間のコミュニケーションは, 認証され保護された Channel を利用して保護するべきである (SHALL).

<!-- Communications between the CSP and the RP SHALL be protected in transit using an authenticated protected channel. -->

CSP は, RP が自身のセキュリティポリシーを適用する際に有用な情報にアクセスできる可能性もある.
こういった情報としては, Device Identity, Location, System Health Check, Configuration Management 等があげられる.
CSP がこういった情報を取得できる場合, Subscriber のプライバシーを侵害しない範囲内で, そういった情報を RP に渡すことも可能であろう.

<!-- Note that the CSP may have access to information that may be useful to the RP in enforcing security policies, such as device identity, location, system health checks, and configuration management. If so, it may be a good idea to pass this information along to the RP within the bounds of the subscriber's privacy preferences. -->

User に関する追加の属性は, Assertion とは別に, RP から CSP への認可されたリクエストを通じてやり取りされてもよい (MAY).
こういった属性へのアクセスに対する認可は, Assertion と一緒に発行することもできる (MAY).
User に関する情報をこのように分離することで, Authentication Assertion 自体には必須な情報のみを含めればよいことになり, ユーザーのプライバシー保護につながる.

<!-- Additional attributes about the user MAY be included outside of the assertion itself as part of a separate authorized request from the RP to the CSP. The authorization for access to these attributes MAY be issued alongside the assertion itself. Splitting user information in this manner can aid in protecting user privacy and allow for limited disclosure of identifying attributes on top of the essential information in the authentication assertion itself. -->

RP は可能な限り全属性ではなく Attribute Claim を要求すべきであり (SHALL), CSP は Attribute Claim をサポートすべきである (SHALL).

<!-- The RP SHALL, where feasible, request attribute claims rather than full attribute values. The CSP SHALL support attribute claims. -->
