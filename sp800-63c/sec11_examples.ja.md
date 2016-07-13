<a name="sec11"></a>

## 11. Assertion Examples

*This section is non-normative.*

本セクションでは SAML (Security Assertion Markup Language) Assertion, Kerberos Ticket, OpenID Connect Token の各種 Assertion について述べる.

<!-- Three types of assertion technologies will be discussed: SAML (Security Assertion Markup Language) assertions, Kerberos tickets, and OpenID Connect tokens. -->

### 11.1. Security Assertion Markup Language (SAML)

SAML はインターネットを介して信頼された主体間で Authentication & Attribute Information を生成・交換するための XML ベースのフレームワークである.
本ドキュメント執筆時の \[[SAML](#SAML)\] 最新仕様は SAML v2.0 (2015年5月15日発行) である.

<!-- SAML is an XML-based framework for creating and exchanging authentication and attribute information between trusted entities over the internet. As of this writing, the latest specification for \[[SAML](#SAML)\] is SAML v2.0, issued 15 March 2005. -->

SAML の構成要素は以下の通りである.

<!-- The building blocks of SAML include: -->

- Assertion の構造を定義する Assertion XML Scheme
- Assertion および Artifact (Section 6.1 で述べた Indirect モードで利用される Assertion の参照) を要求するための SAML Protocol
- SAML の下のレイヤーで利用するコミュニケーションプロトコル (HTTP や SOAP 等) を定義し, SAML Assertion の伝送のために利用される Bindings

<!-- -   the Assertions XML schema which defines the structure of the assertion
-   the SAML Protocols which are used to request assertions and artifacts (the assertion references used in the indirect model described in Section 6.1)
-   the Bindings that define the underlying communication protocols (such as HTTP or SOAP) and can be used to transport the SAML assertions. -->

上記3つの構成要素の組み合わせは SAML Profile と呼ばれ, "Web Browser SSO" などの特定のユースケースに対応する.

<!-- The three components above define a SAML profile that corresponds to a particular use case such as “Web Browser SSO”. -->

SAML Assertion は XML Schema にエンコードされ, 最大3種類の Statement を伝搬するために用いられる.

<!-- SAML Assertions are encoded in an XML schema and can carry up to three types of statements: -->

-   *Authentication statements* は Assertion Issuer, Authenticated Subscriber, 有効期限, およびその他の認証情報を含む.
    例えば, ある Authentication Assertion は, Subscriber "John" が 2004年6月6日の 10:32pm にパスワードを用いて認証されたことを示す, など.
<!-- -   *Authentication statements* include information about the
    assertion issuer, the authenticated subscriber, validity period, and
    other authentication information. For example, an Authentication
    Assertion would state the subscriber “John” was authenticated using a
    password at 10:32pm on 06-06-2004. -->

-   *Attribute statements* は Subscriber に関するその他の詳しい特徴を含む.
    例えば Subject "John" が "Role" 属性に "Manager" という値を持つ, など.
<!-- -   *Attribute statements* contain specific additional characteristics
    related to the subscriber. For example, subject “John” is associated
    with attribute “Role” with value “Manager”. -->

-   *Authorization statements* は Subscriber がアクセスを許可したリソースを特定する.
    リソースとしては特定のデバイス, ファイル, 特定の Web サーバ上の情報などが考えられる.
    例えば, Subject "John" が "Webserver1002" に対する "Read" アクションを "Role" を根拠として許可する, など.
<!-- -   *Authorization statements* identify the resources the subscriber
    has permission to access. These resources may include specific
    devices, files, and information on specific web servers. For
    example, subject “John” for action “Read” on “Webserver1002” given
    evidence “Role”. -->

なお, Authorization Statement は本ドキュメントのスコープ外であり, ここでは議論しない.

<!-- Authorization statements are beyond the scope of this document and will not be discussed. -->

### 11.2. Kerberos Tickets

Kerberos Network Authentication Service \[[RFC 4120](#RFC4120)\] は, ローカルの共有ネットワーク上で共通鍵暗号方式を利用する Client/Server アプリケーションに対して, 強固な認証方式を提供するプロトコルである.
Kerberos では, 拡張仕様によりプロトコル中の特定のステップで公開鍵暗号を利用することもできる.
また Kerberos は Subscriber と RP の間のセッションデータに関する Confidentiality および Integrity を保証することもできる.
Kerberos は Assertion を利用するが, 共有ネットワーク上での利用を想定して設計されたプロトコルであるため, 厳密には Federation Protocol とは言えない.

<!-- The Kerberos Network Authentication Service \[[RFC 4120](#RFC4120)\] was designed to provide strong authentication for client/server applications using symmetric-key cryptography on a local, shared network. Extensions to Kerberos can support the use of public key cryptography for selected steps of the protocol. Kerberos also supports confidentiality and integrity protection of session data between the subscriber and the RP. Even though Kerberos uses assertions, since it is designed for use on shared networks it is not truly a federation protocol. -->

Kerberos は, 信頼できない共有ローカルネットワーク上で, 1つ以上の CSP を利用した Subscriber の認証を可能にする.
Kerberos では, CSP が Subscriber に対して暗号化した状態で発行したランダムな Session Key を Subscriber が復号することにより, 暗黙的に Subscriber が CSP に対して認証したものとする.
(Kerberos の派生プロトコルでは, Subscriber が明示的に CSP に対して認証することを要求するものもあるが, そういったパターンは一般的ではない)
暗号化された Session Key に加え, CSP は Kerberos Ticket と呼ばれる他の暗号化オブジェクトを生成する.
Kerberos Ticket は, Session Key および当該 Session Key の発行対象である Subscriber の Identity, Session Key の有効期限を含む.
チケットは CSP と RP の間での明示的セットアップフェーズで確立された共通鍵を使って Confidentiality と Integrity を保証される.

<!-- Kerberos supports authentication of a subscriber over an untrusted, shared local network using one or more CSPs. The subscriber implicitly authenticates to the CSP by demonstrating the ability to decrypt a random session key encrypted for the subscriber by the CSP. (Some Kerberos variants also require the subscriber to explicitly authenticate to the CSP, but this is not universal.) In addition to the encrypted session key, the CSP also generates another encrypted object called a Kerberos ticket. The ticket contains the same session key, the identity of the subscriber to whom the session key was issued, and an expiration time after which the session key is no longer valid. The ticket is confidentiality and integrity protected by a pre-established that is key shared between the CSP and the RP during an explicit setup phase. -->

Session Key を使って認証するにあたり, Subscriber はチケットを RP に送り, それに添えて Subscriber が当該 Kerberos Ticket に含まれる Session Key の所有者であることを証明する暗号化されたデータも一緒に送る.
Session Key は新しいチケットを生成するのに使われたり, Subscriber と RP の間のコミュニケーションの暗号化および認証のために用いられたりする.

<!-- To authenticate using the session key, the subscriber sends the ticket to the RP along with encrypted data that proves that the subscriber possesses the session key embedded within the Kerberos ticket. Session keys are either used to generate new tickets, or to encrypt and authenticate communications between the subscriber and the RP. -->

一連のプロセスを開始するにあたり, Subscriber は Authentication Server (AS) に Authentication Request を送信する.
AS は, Subscriber の長期間有効なクレデンシャルを用いて Subscriber に紐づく Session Key を暗号化する.
長期間有効なクレデンシャルは AS と Subscriber の間の共通鍵でもよいし, Kerberos における PKINIT 相当の派生パターンでは公開鍵証明書を利用することもできる.
Kerberos 派生プロトコルの多くは, ユーザーが生成したパスワードから導出された Subscriber と CSP の間の共通鍵に依存しているため, 受動的盗聴者によるオフライン辞書攻撃に対して脆弱であることに注意.

<!-- To begin the process, the subscriber sends an authentication request to
the Authentication Server (AS). The AS encrypts a session key for the
subscriber using the subscriber’s long term credential. The long term
credential may either be a secret key shared between the AS and the
subscriber, or in the PKINIT variant of Kerberos, a public key
certificate. It should be noted that most variants of Kerberos based on
a shared secret key between the subscriber and CSP derive this key
from a user generated password. As such, they are vulnerable to offline
dictionary attack by a passive eavesdropper. -->

Session Key を Subscriber に伝送するのに加え, AS は Ticket Granting Server (TGS) と共有されたチケットを発行する.
Verifier は, 明示的な認証を行う代わりに, 当該チケットに含まれる Session Key を使ってチケットを発行するため, このチケットは Ticket Granting Ticket (TGT) と呼ばれる.
TGS は TGT に含まれる Session Key を用いて Subscriber に紐付いた新たな Session Key を暗号化し, RP との共通鍵を使って新しい Session Key に紐付いたチケットを生成する.
Subscriber は Session Key を復号し, チケットと新しい Session Key を使って RP に対して認証を行う.

<!-- In addition to delivering the session key to the subscriber, the AS also
issues a ticket using a key it shares with the Ticket Granting Server
(TGS). This ticket is referred to as a Ticket Granting Ticket (TGT),
since the verifier uses the session key in the TGT to issue tickets
rather than to explicitly authenticate the verifier. The TGS uses the
session key in the TGT to encrypt a new session key for the subscriber
and uses a key it shares with the RP to generate a ticket corresponding
to the new session key. The subscriber decrypts the session key and uses
the ticket and the new session key together to authenticate to the RP. -->

### 11.3. OpenID Connect

OpenID Connect は, OAuth 2.0 Authorization Famework および JSON Object Signing and Encryption (JOSE) をベースとした, インターネットスケールの Federated Identity and Authentication Protocol である.
本ドキュメント執筆時点での最新仕様は version 1.0 with errata (2014年11月8日発行) である.

<!-- OpenID Connect is an internet-scale federated identity and authentication protocol built on top of the OAuth 2.0 authorization framework and the JSON Object Signing and Encryption (JOSE) cryptographic system. As of this writing, the latest specification is version 1.0 with errata, dated November 8, 2014. -->

OpenID Connect は OAuth 2.0 Authorization Protocol の上に定義され, Subscriber が RP に対して Subscriber Identity および Authentication Information にアクセスすることを許可できるようにする.
OpenID Connect では CSP は Identity Provider (IdP) と呼ばれ, OpenID Connect および OAuth 2.0 では RP を Client と呼ぶ.

<!-- OpenID Connect builds on top of the OAuth 2.0 authorization protocol to enable the subscriber to authorize the RP to access the subscriber's identity and authentication information. The CSP in OpenID Connect is known as the identity provider, or IdP. The RP in both OpenID Connect and OAuth 2.0 is known as the client. -->

OpenID Connect のトランザクションでは, IdP は ID Token と呼ばれる JSON Web Token (JWT) 形式の Signed Assertion を発行する.
Client は ID Token をパースして Subscriber および IdP における Primary Authentication Event についての情報を得る.
この ID Token は, 少なくとも Subscriber および Authentication Event に関する以下の Claim を含む.

<!-- In a successful OpenID Connect transaction, the IdP issues an ID Token, which is a signed assertion in JSON Web Token (JWT) format. The client parses the ID Token to learn about the subscriber and primary authentication event at the IdP. This token contains at minimum the following claims about the subscriber and authentication event: -->

 - `iss`: 当該 Assertion を発行した IdP を識別する HTTPS URL.
 - `sub`: Subscriber に紐付いた IdP 固有の Subject Identifier.
 - `aud`: IdP 固有の Audience Identifier. IdP における当該 Client の OAuith 2.0 Client Identifier 値.
 - `exp`: ID Token の有効期限を示す Timestamp. この時刻をすぎて当該 ID Token を受け入れてはならない (MUST NOT).
 - `iat`: ID Token の発行日時を示す Timestamp. この時刻より前に当該 ID Token を受け入れてはならない (MUST NOT).

 <!-- - `iss`: An HTTPS URL identifying the IdP that issued the assertion
 - `sub`: An IdP-specific subject identifier representing the subscriber
 - `aud`: An IdP-specific audience identifier, equal to the OAuth 2.0 client identifier of the client at the IdP
 - `exp`: The timestamp at which the ID Token expires and after which MUST NOT be accepted the client
 - `iat`: The timestamp at which the ID Token was issued and before which MUST NOT be accepted by the client -->

ID Token に加え, IdP は Client に対して OAuth 2.0 Access Token を発行する.
この Access Token は IdP の UserInfo Endpoint にアクセスするために利用できる.
UserInfo Endpoint は Subscriber に関する一連の Claim を含んだ JSON Object を返す.
ここで返される Claim としては, 氏名, Email アドレス, 住所, 電話番号, その他のプロフィール情報等が挙げられる.
ID Token に含まれる情報は Authentication Event を反映したものであるが, UserInfo Endpoint から返される情報は一般的には不変かつさまざまな目的で利用できるものである.
UserInfo から返されるそれぞれの Claim へのアクセス権限は, 特別に定義された OAuth Scope を使って管理される.
OpenID Connect が定義するそういった Scope としては, `openid`, `profile`, `email`, `phone`, `address` が挙げられる.
また, `offline_access` という Scope を用いて, Refresh Token の発行をリクエストすることができる.
Refresh Token を利用すると, RP は Subscriber がその場にいない時でも UserInfo Endpoint にアクセスすることができる.

<!-- In addition to the ID Token, the IdP also issues the client an OAuth 2.0 access token which can be used to access the UserInfo Endpoint at the IdP. This endpoint returns a JSON object representing a set of claims about the subscriber, including but not limited to their name, email address, physical address, phone number, and other profile information. While the information inside the ID Token is reflective of the authentication event, the information in the UserInfo Endpoint is generally more stable and could be more general purpose. Access to different claims from the UserInfo Endpoint is governed by the use of a specially defined set of OAuth scopes, `openid`, `profile`, `email`, `phone`, and `address`. An additional scope, `offline_access`, is used to govern the issuance of refresh tokens, which allow the RP to access the UserInfo Endpoint when the subscriber is not present. -->
