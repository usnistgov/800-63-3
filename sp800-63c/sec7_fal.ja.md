<a name="fal"></a>

## 7. Federation Assurance Level (FAL)

本セクションでは Federation and Assertion Level, もしくは FAL を定義する.
FAL はあるトランザクションで利用されている Assertion と Federation Protocol の特徴を記述するものである.
RP が当該トランザクションにおける要求レベルを明示したり, RP と CSP が当該トランザクションにおける必要レベルをあらかじめ設定しておいたりといった利用方法が想定される.

<!-- This section defines a Federation and Assertion Level, or FAL. The FAL describes aspects of the assertion and federation protocol used in a given transaction. These levels can be requested by an RP or required by configuration of both RP and CSP for a given transaction. -->

FAL は [federation model](#sec4), [assertion protection strength](#sec5), および [assertion presentation](#sec6) を統合し, スカラーで比較可能な値としたものである.
他の様々な要素を組み合わせることも可能だが, FAL の上記3要素を用いて段階的によりセキュアな実装方法の選択肢を提示することにより, 実装ガイドラインとして分かりやすいものを作ることを意図している.
一連の各レベルは, そのレベル以下の要件をすべて満たすものとする.
FAL のリストに無いような組み合わせも可能であるが, 本ドキュメントではそういった組み合わせは対象としない.

<!-- The FAL combines aspects of [federation model](#sec4), [assertion protection strength](#sec5), and [assertion presentation](#sec6) into a single, increasing scale. While many other combinations of factors are possible, this list is intended to provide clear implementation guidelines representing increasingly secure deployment choices. Each successive level subsumes and fulfills all requirements of lower levels. Such definitions not found in the FAL table are possible but outside the scope of this document. -->

|FAL|Requirement|
|:--:|----|
|1|Bearer assertion, direct presentation, asymmetrically signed by CSP|
|2|Bearer assertion, indirect presentation, asymmetrically signed by CSP|
|3|Bearer assertion, indirect presentation, asymmetrically signed by CSP and encrypted to RP|
|4|Holder of key assertion, indirect presentation, asymmetrically signed by CSP and encrypted to RP|

例えば, FAL 1 は OpenID Connect Implicit Client Profile や SAML Web SSO Profile 等に相当する.
FAL 2 は OpenID Connect Basic Client Profile, SAML Artifact Binding Profile 等に相当する.
FAL 3 では, FAL 2 に加えて, OpenID Connect ID Token や SAML Assertion を当該 RP の公開鍵で暗号化することといった要件が加わる.
FAL 4 では, FAL 3 に加えて, Assertion に紐付いた鍵 (FIDO Token 等) の提示が要求される.

<!-- For example, FAL 1 maps to the OpenID Connect Implicit Client profile or the SAML Web SSO profile, with no additional features. FAL 2 maps to the OpenID Connect Basic Client profile or the SAML Artifact Binding profile, with no additional features. FAL 3 additionally requires that the OpenID Connect ID Token or SAML Assertion be encrypted to a public key representing the RP in question. FAL 4 requires the presentation of an additional key bound to the assertion (for example, a FIDO token) along with all requirements of FAL3. -->

どんなプロトコルであれど, Federation Protocol の一部として Assertion の性質に着目すれば, RP はそれがどの FAL レベルに相当するかを簡単に特定できる.
したがって, 当該認証トランザクションで要求すべき FAL の決定や, 実際にそのトランザクションが当該 FAL に適合しているかの検証は, RP の責務である.

<!-- Regardless of what is requested or required by the protocol, the applicable FAL is easily detected by the RP by observing the nature of the assertion as it is presented as part of the federation protocol. Therefore, the RP is responsible for determining which FALs it is willing to accept for a given authentication transaction and ensuring that the transaction meets the requirements of that FAL. -->