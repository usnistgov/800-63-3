<a name="sec1"></a>
<!--
## 1. Purpose
-->

## 1. 目的

<!--This recommendation and its companion documents, [SP 800-63-3](sp800-63-3.html), [SP 800-63A](sp800-63a.html), and [SP 800-63C](sp800-63c.html), provide technical guidelines to credential service providers for the implementation of digital authentication.-->

本推奨、及び付随文書 [SP 800-63-3](sp800-63-3.html), [SP 800-63A](sp800-63a.html) 及び [SP 800-63C](sp800-63c.html) は、クレデンシャル・サービス・プロバイダがデジタル認証の実装を行う際の技術的なガイドラインを提供する。

<a name="sec2"></a>

<!--
## 2. Introduction
-->

## 2. イントロダクション

<!--
Digital authentication is the process of establishing confidence in user identities electronically presented to an information system. E-authentication presents a technical challenge when this process involves the digital authentication of individual people over a network.
-->

デジタル認証は、情報システムにおいて電子的に表現されたユーザのアイデンティティの確かさを証明するためのプロセスである。E-authentiationは、本プロセスがネットワークを介した個々人のデジタル認証に関与する際、技術的なチャレンジを提起する。

<!--TODO E-Authentication -->

<!--
The ongoing authentication of subscribers is central to this process. Subscriber authentication is performed by verifying that the claimant controls one or more *authenticators* (called *tokens* in earlier editions of SP 800-63) associated with a given subscriber. A successful authentication results in the assertion of an identifier, either pseudonymous or non-pseudonymous, and optionally other identity information, to the relying party (RP).
-->

継続的に行われる加入者の認証が本プロセスの中心である。加入者認証は、要求者が、加入者と関連付けられた一つ以上の *認証器* (SP 800-63の以前の版では *トークン* と呼ばれていた)を制御していることを検証することによって実施される。認証が成功すると、識別子（仮名または仮名でない）及びオプションで他のアイデンティティ情報のアサーションが、リライング・パーティ(RP: Relying Party)に提示される。


<!--This document provides guidance on types of authentication processes, including choices of authenticators, that may be used at various *Authenticator Assurance Levels* (AAL). It also provides guidance on the lifecycle of authenticators, including revocation in the event of loss or theft.-->

本書は、様々な *認証器信頼レベル* (AAL)の認証器の選択を含む、認証プロセスの種別の指針を提供する。また、本書は認証器の紛失・盗難に伴う廃棄を含む、認証器のライフサイクルに関する指針を提供する。

<!--
These technical guidelines apply to digital authentication of human users to IT systems over a network. They do not primarily address the authentication of a person who is physically present, for example, for access to buildings, although some credentials that are used remotely may also be used in local authentication. These technical guidelines also establish requirements that Federal IT systems and service providers participating in authentication protocols be authenticated to subscribers. However, these guidelines do not specifically address machine-to-machine (such as router-to-router) authentication, or establish specific requirements for issuing authentication credentials to machines and servers when they are used in e-authentication protocols with people.
-->

これらの技術的なガイドラインは人間のユーザがネットワークを介してITシステムに対して行うデジタル認証に適用される。これらは主として人間が物理的に存在すること ー例えばそのユーザが建物に入館できることー の認証については言及しない。しかしながら、リモートで利用されるクレデンシャルのなかにはローカルの認証でも利用するものがあるかもしれない。また、これらの技術的なガイドラインは、米国連邦のITシステムやサービスプロバイダが加入者を認証するための認証プロトコルに準拠する上での要件を規定している。しかしながら、これらのガイドラインは、(ルータ同士のような)Machine-to-machineの認証については言及していない。また、マシンやサーバに対して発行された認証クレデンシャルが、E-authenticationプロトコル中でユーザを介して利用される際の特別な要件については規定しない。

<!--TODO E-authentication-->

<!--
The strength of an authentication transaction is characterized by a categorization known as the AAL. A high-level summary of the technical requirements for each of the authenticator assurance levels is provided below; see [Section 4](#sec4) and [5](#sec5) of this document for specific normative requirements.
-->

認証トランザクションの強度はAALとして知られている分類によって特徴付けられる。個々の認証器信頼レベルに求められる技術要件の高度なサマリを以下に記載する; 特別な要求規則については、本書の [Section 4](#sec4) 及び [5](#sec5) を参照。

<!--
**Authenticator Assurance Level 1** - AAL 1 provides single factor authentication, giving some assurance that the same claimant who participated in previous transactions is accessing the protected transaction or data. AAL 1 allows a wide range of available authentication technologies to be employed and requires only a single authentication factor to be used. It also permits the use of any of the authentication methods of higher authenticator assurance levels, therefore allowing CSPs to allow users to use a higher AAL authenticator to be at AAL 1. Successful authentication requires that the claimant prove through a secure authentication protocol that he or she possesses and controls the authenticator.
-->

**認証器信頼レベル1** - AAL 1は単一要素の認証を提供する。これは、保護された取引/データへアクセスしようとする要求者が以前の取引に関わった人と同一であるという、ある程度の信頼性を持つ。AAL 1は幅広く利用可能な認証技術の採用を認めており、単一要素の認証の利用のみを要求している。したがって、CSPに対し、ユーザがより高度なAALの認証器をAAL 1の用途で利用することを認めている。認証が成功するには、その要求者が、セキュアな認証プロトコルを介して、自身がその認証器を所有・制御していることを証明する必要がある。

<!--
**Authenticator Assurance Level 2** – AAL 2 provides higher assurance that the same claimant who participated in previous transactions is accessing the protected transaction or data. At least two different authentication factors SHALL be used. AAL 2 also permits any of the authentication methods of AAL 3 for the same reasons as AAL 1. AAL 2 authentication requires cryptographic mechanisms that protect the primary authenticator against compromise by the protocol threats for all threats at AAL 1 as well as verifier impersonation attacks. Approved cryptographic techniques SHALL be used at AAL 2 and above.
-->

**認証器信頼レベル2** - AAL 2は、少なくとも2つの異なる要素の認証を利用するものとする(SHALL)。これは、保護された取引/データへアクセスしようとする要求者が以前の取引に関わった人と同一であるということに対して、より高い信頼性を提供する。AAL 2 もまた AAL 1の場合と同様の理由で、AAL 3の認証手段を利用することを許可する。AAL 2認証では、暗号メカニズムを用いて、認証器なりしまし攻撃のようなAAL 1における全ての脅威から生じるプロトコル上のセキュリティ侵害に対し、最も重要な認証器を保護することが要求される。

<!--
**Authentication Assurance Level 3** – AAL 3 is intended to provide the highest practical remote network authentication assurance. Authentication at AAL 3 is based on proof of possession of a key in a physical authenticator through a cryptographic protocol. AAL 3 is similar to AAL 2 except that only multifactor hardware cryptographic authenticators are allowed. The authenticator SHALL be a hardware cryptographic module validated at Federal Information Processing Standard (FIPS) 140 Level 2 or higher overall with at least FIPS 140 Level 3 physical security.
-->

**認証器信頼レベル 3** - AAL 3は、リモートネットワークにおける実現しうる最も高い認証信頼性を提供することを目的としている。AAL 3は、暗号プロトコルを介した、物理的な認証器に格納されている鍵の所有証明(proof of posession)に基づいたものである。AAL 3は、多要素ハードウェア暗号化認証器(multifactor hardware cryptographic authenticator)だけが認められているということを除けば、AAL 2と同様である。認証器は、連邦情報処理標準(FIPS) 140 Level 2、または少なくともFIPS 140 Level 3の物理セキュリティを確保しているような高度な基準で検証されたハードウェア暗号化装置であるものとする(SHALL)。


