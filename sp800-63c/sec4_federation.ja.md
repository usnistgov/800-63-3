<a name="sec4"></a>

## 4. Federation

Identity / Authentication Information を一連のネットワークシステム間でやりとりするためのプロセス.
Federation シナリオでは, Verifier / CSP は一般的に Identity Provider や IdP と呼ばれる.

<!-- Federation is a process that allows for the conveyance of identity and authentication information across a set of networked systems. In a federation scenario, the verifier or CSP is often known as the *identity provider*, or IdP. -->

![Figure 1: Federation](sp800-63c/media/federation.png)

**Figure 1: Federation**

Federation Protocol では, Subscriber, CSP, RP の3者間で三角形の関係がなりたつ.
プロトコルによっては, 異なるタイミングで異なる情報が各辺を流れることもある.
Subscriber は, 通常は Web Browser を通じて CSP, RP 双方とやり取りを行う.
RP と CSP の間のやりとりは, (Subscriber が関与するリダイレクト経由で) 間接的に行われることもあれば, (Back-channel で) 直接的に行われることもあり, (暗号論的に保護された Self-contained Assertion などのように) パッケージ化された情報を通じて行われることもある.

<!-- In a federation protocol, a triangle is formed between the subscriber, the CSP, and the RP (Figure 1). Depending on the specifics of the protocol, different information passes across each leg of the triangle at different times. The subscriber communicates with both the CSP and the RP, usually through a web browser. The RP communicates with the CSP, though this communication can happen indirectly (through redirects involving the subscriber), directly (through a back-channel connection), or via a packaged information bundle (such as a cryptographically protected and self-contained assertion). -->

Subscriber は CSP に対して何らかの Primary Credential を使って自身を認証し, その Authentication Event はネットワーク経由で RP に対して Assert される.
CSP はこのプロセスを通じて Subscriber に関する Attribute Statement を生成することも可能である.
この Attribute および Authentication Event は通常 Assertion を利用して RP に伝えられる. (Section 5 参照)

<!-- The subscriber authenticates to the CSP using some form of primary credential, and then that authentication event is asserted to the RP across the network. The CSP can also make attribute statements about the subscriber as part of this process. These attributes and authentication event information are usually carried to the RP through the use of an assertion (see section 5.). -->

RP と CSP とのやりとりは, Subscriber がトランザクションを行う CSP には明示される.
複数の RP とやりとりする CSP は Subscriber のトランザクションをプロファイリングすることも可能となる.
これは Federation 無しには不可能であったろう.
これは Subscriber の Privacy Interest にそぐわない形での Subscriber Tracking や Profile Information の利用につながりかねない.

<!-- The RP communication with the CSP reveals to the CSP where the subscriber is conducting a transaction. Communications from multiple RPs allow the CSP to build a profile of subscriber transactions that would not have existed absent federation. This aggregation could enable new capabilities for subscriber tracking and use of profile information that do not align with the privacy interests of the subscribers. -->

CSP は Subscriber と RP のやりとりを第三者に漏らすべきではなく (SHALL NOT), Federated Authentication 目的や法的手続き以外でそういった情報を利用すべきでもない (SHALL NOT).
CSP は Subscriber Tracking や Profiling を防止したり Unlinkability を確保するための技術的対策を行うべきである (SHOULD).

<!-- The CSP SHALL not disclose information on subscriber activities with an RP to any party, nor use the
information for any purpose other than federated authentication or to comply with law or legal process. The CSP SHOULD employ technical measures to provide unlinkability and prevent subscriber activity tracking and profiling. -->

### 4.1. Federation Models

本セクションでは, 現在使われているいくつかの Identity Federation の一般的モデルを概観する.
これらのモデルでは, Federation 関係主体間の Trust 確立方法が複数種類存在する.
なかには高レベルの Trust を必須とするモデルもあり, 多様な Trust Relationship を認めるモデルもある.

<!-- This section provides an overview of a few common models of identity federation currently in use. In these models, trust is established between members of the federation in several different ways. Some models mandate that federated parties have a high level of trust. Other models allow for parties with a diversity of trust relationships. -->

#### 4.1.1 Central Authority

Central Authority に対する Trust を前提として, 相互に Trust を確立しメタデータのやりとりを行う Federated Party も存在する.
そういったモデルでは, Central Authority は Federation を行う各主体に対して一定レベルの審査を行い, Security および Integrity Standard に対する準拠を求めることが多い.

<!-- Some federated parties trust a central authority to make trust decisions for them and communicate metadata between parties. In this model, the central authority generally conducts some level of vetting on each party in the federation to verify compliance with predetermined security and integrity standards. -->

Central Authority モデルを用いた Federation の多くでは, Federation に参加しているか否かという単一レベルの Trust のみが存在する.
しかしながら, より洗練した Federation ではより細かな Trust レベルを持ち, より細かく徹底した審査を通過した主体やより高い Trust レベルを満たす主体を扱うことができる.
高レベルの Trust を実現できれば, そういった高レベルな主体に対しては情報を自動的に渡すといったことも可能になる.

<!-- Most federations using the central authority model have a single level of trust - either parties are in the federation or they are not. However, more sophisticated federations have multiple tiers of trust which can be used by federated parties to tell whether other parties in the federation have been more thoroughly vetted or have some common purpose that justifies a higher level of trust. This higher level of trust makes some parties in the federation more likely to automatically release information about their users to the parties in the higher tiers. -->

#### 4.1.2 Manual Registration

Manual Registration モデルでは, System Administorator がメタデータを扱い, システムの相互接続性をテストしたのち, 実際に User Transaction を開始させる.
Federation に参加する主体に関するメタデータは Federated Party のレジストリに手動入力される.
各主体は個別に自身がやりとりする相手を登録したレジストリを管理し, そのレジストリに登録されている相手とは Trust が確立されたとみなす.

<!-- In the manual registration model of federation, system administrators communicate metadata and test system interoperability before transactions take place between users over the wire. Metadata for each party who wishes to participate is manually input into a registry of federated parties. Each party maintains their own registry of other parties whom they have deemed trustworthy. -->

Manual Registration は, Authority や Federation Operator の関与無しに, 個別に行うことができる.
この場合, CSP と RP の間にはすでに Trust Relationship が確立されていることであろう.

<!-- Manual registration can take place on a case by case basis without any authority or federation operator in place. In this case, an existing pairwise trust relationship is generally already in place between the CSP and the RP. -->

Manual Registration は Central Authority モデルと合わせて利用することもできる.
その場合, Central Authority と Trust 関係にある主体を含んだレジストリが事前に構築され, それ以降は必要に応じて手動でのレジストリ登録が行われることになる.

<!-- Manual registration can work in concert with a central authority model. In this case, a registry is pre-populated with parties trusted by the central authority, and more parties are added manually on an as-needed basis. -->

#### 4.1.3 Dynamic Registration

Dynamic Registration モデルでは, 各システムはその他のシステムが当該システムのメタデータを取得できるように well-known location エンドポイントを持つ.
また新しいシステムが人間の関与無しに自身を登録できるよう, 予測可能な形で API エンドポイントも提供する.
Dynamic Registration を使うシステムは, Subscriber に CSP 上で Identity Federation Transaction に対する明示的許可を要求するなど, 人間が関与する検証ステップを設けるべきである (SHOULD).

<!-- In the dynamic registration model of federation, systems have a well-known location where other systems can find their metadata. They also have predictable API endpoints where new systems can register themselves without human involvement. Systems that make use of dynamic registration SHOULD require verifiable human interaction, such as the approval of the identity federation transaction by the authenticated subscriber at the CSP. -->

Dynamic Registration モデルでは, 各主体は事前に相互の Trust を確立できないことが多く, デフォルトではあまり多くの情報をやりとりしないことが多い.
この問題は, Software Statement と呼ばれる技術を用いれば, ある程度改善される.
Software Statement とは, Dynamic Registration に関与した主体に関する属性を暗号論的に検証可能とするものである.
Software Statement は RP Software に関する属性のリストであり, 認証機関により暗号論的に署名されている.
認証機関を信頼する主体は, 認証機関に対する Trust を Dynamic Registration によって確立したパートナーシップに対しても拡張できる.
これにより Federated Party 間で Trust を確立したり強めたりすることができる.

<!-- Frequently, parties in a dynamic registration model have no way to trust each other ahead of time, so little information is exchanged by default. This problem is somewhat mitigated by a technology called software statements, which allow federated parties to cryptographically verify some attributes of the parties involved in dynamic registration. Software statements are lists of attributes describing the RP software, cryptographically signed by certifying bodies. Because both parties trust the certifying body, that trust can be extended to the other party in the dynamic registration partnership.  This allows trust to be established or elevated between the federating parties. -->

一定レベルの Trust を確保した状態で Dynamic Registration を利用可能な相手を Whitelist で管理する場合もある.
同時に, Blacklist を利用して, 低レベルの Trust 関係で Dynamic Registration をさせる相手を管理したり Dynamic Registration を禁止したりすることもある.
Whitelist や Blacklist にないものは "Glaylist" にあるものとみなされ, そういった主体は, 一般的に人間によるレビューを経るまで低レベルの Trust を強いられることになる.

<!-- Many federated parties establish whitelists of other federated parties who may dynamically register with some predetermined level of trust. They also establish blacklists of federated parties who may be allowed dynamically register with a low level of trust, or who may not be allowed to dynamically register at all. Everything that is not on a whitelist or a blacklist can be considered to be in a gray area or on a "graylist." Graylisted parties generally start out with a low level of trust until they can be reviewed by a human who can determine an appropriate level of trust. -->

#### 4.1.4 Brokered Federation

このモデルでは, 3rd-party がすべてのトランザクションに中間者として介在し, CSP と RP の間で Authentication Event の成否を伝搬する.
Broker は片や Federation CSP として動作し, もう片方では Federation RP として動作する.
よって本チャプターで述べる CSP および RP に適用される Normative / Non-normative Requirements は, 同様に Broker にも適用されるべきである (SHALL).

<!-- In this model, a third-party sits in the middle of the transaction and communicates the success or failure of an authentication event at the CSP to the RP. Effectively, a broker functions as a federation CSP on one side and a federation RP on the other side. Therefore, all normative and non-normative requirements that apply to CSPs and RPs in this chapter SHALL apply to the broker. -->

![Figure 2: Broker](sp800-63c/media/broker.png)

**Figure 2: Broker**


Broker の介在により, RP と CSP の間のやりとりは簡素化され, 技術的に単純になる.
また Broker はトランザクションの両端の主体を Blinding した状態での Assertion のやりとりを可能とするため, Business Confidentiality と Privacy Risk 低減にもつながる.
例えば, 相互に Subscriber リストを開示したくはない Organization が Federation を行う場合や, 相互の Blinding が CSP や RP による Subscriber の Tracking / Profiling を防止する場合などが例として挙げられる.
しかしながらこのモデルではそういった能力を Broker が持つことになる.

<!-- Brokers can enable simplified technical integrations between the RP and CSP by eliminating the need for multiple point to point integrations. Brokers can also provide business confidentiality and mitigate some of the privacy risks of point to point federation described above by passing the assertions while blinding the participants on either side of the transaction to each other. For example, organizations may not wish to reveal their subscriber lists to each other and blinding prevents the capability for CSPs or RPs to track and profile subscribers. However, this model transfers this capability to the broker. -->

多様な Privacy 保護レベルを実現する Blinding 技術が存在するが, Blinding レベルが上がると技術的複雑度は上昇する.
Privacy Policy で CSP, RP, Broker による適切な利用を宣言していたとしても, Blinding 技術はデータを利用不可とするため効率的とは言い難い.

<!-- There is a spectrum of blinding technologies that offer varying levels of privacy protection. However, as the level of blinding increases, so does the technical implementation complexity. Although privacy policies may dictate appropriate use by the CSP, RP, and the broker, blinding technology is far more effective, by making the data unavailable. -->

1. Broker は RP と CSP を相互に Blind しない. Broker は Subscriber と RP, CSP の関係性を監視・追跡可能であり, Assertion を通じてやりとりされるすべての属性を見ることができる.

<!-- 1. The broker does not blind the RP and CSP from one another. The broker is able to monitor and track all subscriber relationships between the RPs and CSPs, and has visibility into any attributes it is transmitting in the assertion. -->

2. Broker は RP と CSP を相互に Blind しない. Broker は Subscriber と RP, CSP の関係性を監視・追跡可能であるが, Assertion の中身を見ることはできない.

<!-- 2. The broker does not blind the RP and CSP from one another. The broker is able to monitor and track all subscriber relationships between the RPs and CSPs, but has no visibility into any attributes it is transmitting in the assertion. -->

3. Broker は RP と CSP を相互に Blind する. Broker は Subscriber と RP, CSP の関係性を監視・追跡可能であり, Assertion を通じてやりとりされるすべての属性を見ることができる.

<!-- 3. The broker blinds the RP and CSP from each other. The broker is able to monitor and track all subscriber relationships between the RPs and CSPs, and has visibility into any attributes it is transmitting in the assertion. -->

4. Broker は RP と CSP を相互に Blind する. Broker は Subscriber と RP, CSP の関係性を監視・追跡可能であるが, Assertion の中身を見ることはできない.

<!-- 4. The broker blinds the RP and CSP from each other. The broker is able to monitor and track all subscriber relationships between the RPs and CSPs, but has no visibility into any attributes it is transmitting in the assertion. -->

5. Broker は RP と CSP および Broker 自身を Blind する. Broker は一切の Subscriber の関係性を監視・追跡することができず, Assertion の中身を見ることもできない.

<!-- 5. The broker blinds the RP, CSP, and itself. The broker cannot monitor or track any subscriber relationships, and has no visibility into any attributes it is transmitting in the assertion. -->
