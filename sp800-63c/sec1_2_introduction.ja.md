<a name="sec1"></a>

## 1. Purpose

本ドキュメントおよび SP 800-63-3, SP 800-63A, SP 800-63B は, リモートでの認証を実装する際の Credential Service Provider の技術ガイダンスである.

<a name="sec2"></a>

## 2. Introduction

Assertion は Credential Service Provider (CSP) から Relying Party (RP) に対して提示される, ある Subscriber に関する情報を含む Statement である.
Assertion は RP と Verifier がお互いに離れた場所にいる場合に用いられる (例: 両者が共有ネットワークやインターネットを通じて接続されているなど).
RP は Assertion に含まれる情報を使って Subscriber を識別し, RP の管理下にあるリソースに対する Subscriber のアクセスを制御する.
Assertion は Subscriber についての Identification / Authentication Statement を含むこともあり, Subscriber のその他の属性を含むこともありうる.
それらの情報は RP が Authorization Decision を下す際の手助けとなる.

<!-- Assertions are statements from a credential service provider (CSP) to a relying party (RP) that contain information about a subscriber. Assertions are used when the RP and the verifier are not co-located (i.e., they are connected through a shared network or the internet). The RP uses the information in the assertion to identify the subscriber and make authorization decisions about their access to resources controlled by the RP. An assertion may include identification and authentication statements regarding the subscriber and may additionally include attribute statements that further characterize the subscriber and support the authorization decision at the RP. -->

Assertion は Identity Federation Protocol を使ってネットワーク越しに提示される.
Federation Protocol では, Subscriber は Credential を使って RP に直接認証をすることはなく, Federation Protocol の定める方法により CSP が生成した Assertion を提示することで RP に認証を行う.
またその際 CSP が Subscriber を認証することになる.
この仕組みを利用すると, CSP に一度認証を行えば, それ以降複数の RP に対して個別の Credential を必要とせずにサービス提供を受けることができるようになるため, Single Sign On の実現にもつながる.

<!-- Assertions are presented over a network through the use of an identity federation protocol. In a federation protocol, the subscriber does not authenticate directly to the RP using credentials as described in this document suite. Instead, the federation protocol defines a mechanism for an RP to request that a CSP generate an assertion for the currently-present subscriber, by way of having the subscriber authenticate to the CSP. This supports the process of Single Sign On, allowing subscribers to authenticate once to a CSP and subsequently obtain services from multiple RPs, all without requiring the subscriber to hold or maintain separate credentials at each RP. -->

また, Assertion Mechanism は Subscriber の属性・特徴ベースの認証スキーマを促進するものでもある.
属性はしばしば Attribute Based Access Control (ABAC) や Role Based Access Control (RBAC) といったアクセスコントロール手法の中で, アクセス権限を決定する際に用いられる.

<!-- Assertion mechanisms can also facilitate authentication schemes that are based on the attributes or characteristics of the subscriber. Attributes are often used in determining access privileges for Attribute Based Access Control (ABAC) or Role Based Access Control (RBAC). -->

Assertion Scheme は一般的にかなり複雑な Multiparty Protocol であるため, 満たすべき Security Requirements も多岐にわたる.
ある Assertion Scheme を評価する際は, その Scheme に含まれる Interaction を分解し, 個別に分析してゆくことが有効な手段となる.
一般的に, Subscriber (User) <-> CSP 間の Interaction と Subscriber <-> RP 間の Interaction は 800-63B で示された認証方式と類似したものとなり, CSP <-> RP 間の Interaction は SP 800-63A で示された手順によって確立された属性などを運搬するものとなる.
したがって, 本ドキュメントで示される Requirements は, 上記2つのドキュメントと相通じるものがある.

<!-- It is important to note that assertion schemes are fairly complex multiparty protocols, and therefore have fairly subtle security requirements which must be satisfied. When evaluating a particular assertion scheme, it may be instructive to break it down into its component interactions. Generally speaking, interactions between the user subscriber and the CSP and between the subscriber and RP are similar to the authentication mechanisms presented SP 800-63B, while interactions between the CSP and RP convey attributes such as those established using procedures in SP 800-63A. Many of the requirements presented in this document will, therefore, have some relationship with corresponding requirements in those two documents. -->
