```

����֧��OAuth2.0���û�ָ�ϡ�����OAuth1.0��һ�ж��ǲ�ͬ�ģ����Կ������û�ָ�ϡ�
���û�ָ�Ϸ�Ϊ�������֣���һ������OAuth2.0�ṩ�ˣ�OAuth 2.0 Provider�����ڶ�������OAuth2.0�Ŀͻ��ˣ�OAuth 2.0 Client��
OAuth2.0�ṩ��

OAuth2.0���ṩ�˵���;�Ǹ����ܱ�������Դ��¶��ȥ�����ð�������һ�����Է����ܱ�������Դ�Ŀͻ��˴����ṩ����ͨ���������֤�����ڷ����ܱ�������Դ��OAuth 2���������ġ����ʵ��ĵط����ṩ��Ҳ����Ϊ�û��ṩһ������ȷ�Ͽͻ��� �Ƿ��ܹ������ܱ�������Դ�Ľӿڣ�Ҳ����һ��ҳ�����һ�����ڣ���
Knowvin
Knowvin

�� OAuth 2 �ṩ����ʵ�Ƿֳ���Ȩ�������Դ����������ɫ�ģ�����������ɫ��ʱ�Ǵ�����ͬһ��Ӧ�ó����еģ�ͨ�� Spring Security OAuth �������ѡ��Ľ����Ƿ��ѵ�����Ӧ�ó����У�Ҳ������ѡ��ĸ���Ȩ�������ö����Դ���񡣻�ȡ���ƣ�Tokens������������Spring MVC�Ŀ������˵�������ģ������ܱ�������Դ��ͨ����׼��Spring Security���������������ġ�
�����оٵĶ˵��� Spring Security ��������ʵ�� OAuth 2 ��Ȩ����������Ķ˵㣺
AuthorizationEndpoint  ��������Ȩ��������ġ�Ĭ�ϵ�URL�ǣ�/oauth/authrize��
TokenEndpoint  �����ڻ�ȡ�������ƣ�Access Tokens��������Ĭ�ϵ�URL�ǣ�/oauth/token��
�����������ʵ��һ��OAuth2��Դ������������ģ�
OAuth2AuthenticationProcessingFilter ��������������ڼ��������ṩ��һ����Ȩ�˵ķ��������Ƿ���Ч��
�������е�OAuth 2.0���ṩ�ˣ�ͨ��ʹ��Spring OAuthר�ŵ�@Configuration�������������á�Ҳ����ͨ��XML�����ռ�������OAuth��XML��schema���ڣ�http://www.springframework.org/schema/security/spring-security-oauth2.xsd������ռ���http://www.springframework.org/schema/security/oauth2

������Ȩ������ʱ,�����뿼�ǵ�grant���ͣ����ն��û��ǣ��ͻ��˻�ʹ�û�ȡ���ķ�������(����Ȩ���롢�û�ƾ֤��ˢ������)���������������������ṩһЩʵ�֣���ͻ���ϸ�ڷ�������Ʒ��������û����ĳЩ�����ȫ����ơ�������ע��,ÿ���ͻ��˿���ר������Ȩ���ܹ�ʹ��ĳЩ��Ȩ���ƺͷ�����Ȩ����������Ϊ�����ṩ������Ϊ֧�֡��ͻ�֤�顱grant����,������ζ��һ���ض��Ŀͻ��˱���Ȩʹ��grant���͡�

@EnableAuthorizationServer ע���������� OAuth 2.0 ��Ȩ���������ƣ���������һ��
@Beans ȥʵ�� AuthorizationServerConfigurer (����һ��hander������ʵ�ֵĿշ���)��
���¹���ί�и��� spring ����Ķ��� configurers ���Ҵ��ݵ� AuthorizationServerConfigurer��
ClientDetailsServiceConfigurer:
���configurer�����˿ͻ���ϸ�ڷ���
�ͻ���ϸ��Ϣ���Ա���ʼ��,��������Բο����е��̵ꡣ
AuthorizationServerSecurityConfigurer:�����ƶ˵��϶����˰�ȫԼ����
AuthorizationServerEndpointsConfigurer:��������Ȩ�����ƶ˵�����Ʒ���

�ṩ����������Ҫ��һ�����ṩ��OAuth �ͻ��˵���Ȩ�롣 OAuth �ͻ���ͨ�����ն��û�����һ����������֤��/�������Ȩ��֤ҳ������ȡ��Ȩ�룬Ȼ�󣬽���Ȩ�봫�ݸ��ṩ����Ȩ����������������֤���ض���ҳ�档 �� OAuth 2 ˵���ĵ�������ϸ��ʾ����
�� xml �����ļ��У�����ʹ��<authorization-server/>�ڵ����� OAuth 2.0 ��Ȩ��������


ClientDetailsServiceConfigurer �ࣨAuthorizationServerConfigurer���е�һ�������ࣩ������������һ�������ڴ�Ļ���JDBC�Ŀͻ�����Ϣ���� 
�ͻ��˶�����Ҫ�������У�
clientId�������룩�ͻ���id��
secret�������ڿ����εĿͻ����Ǳ���ģ��ͻ��˵�˽����Ϣ��
scope���ͻ��˵����������scopeδ�������Ϊ�գ�Ĭ��ֵ������ͻ��������������ơ�
authorizedGrantTypes����Ȩ���ͻ���ʹ�õ�Ȩ�����͡�Ĭ��ֵΪ�ա�
authorities����Ȩ���ͻ��˵�Ȩ�ޣ�Spring��ͨ�İ�ȫȨ�ޣ���
�����е�Ӧ���У�����ͨ��ֱ�ӷ������صĴ洢�ļ����磺JdbcClientDetailsService���õ������ݿ������ͨ��ʵ��ClientDetailsManager �ӿڣ�Ҳ����ʵ��ClientDetailsService �ӿڣ�����ʵ�������ӿڣ������¿ͻ�����Ϣ��

AuthorizationServerTokenServices �ӿ��ﶨ���� OAuth 2.0 ���ƵĲ��������� ע�����¼��㣺
����һ����������ʱ�����뱣��Ȩ����Ϣ�������������Ʋſ�����������
�����������ڼ��ش�������ʱ����Ȩ��Ϣ��
����AuthorizationServerTokenServices �ӿڵ�ʵ����ʱ������Կ���ʹ��DefaultTokenServices �࣬��ʹ�����ֵ�������ƣ����������������������������ƣ������������ƣ���ί��TokenStore����д��� ����Ĭ�ϲ��û����ڴ�ʵ�ֵĴ洢��ʽ����Ҳ��һЩ�����Ĵ洢��ʽ�� ����������һЩ��ʽ�ļ�飺
Ĭ�ϵ�InMemoryTokenStore ��������ڵ������������ǳ����ã��ŵ��У���������崻�ʱ�������л������ݷ����������󲿷���Ŀ�����ڿ�ʼʱ�����ڿ���ģʽ��ʹ�����ַ�ʽ�������Ƚ���������һ��û�����������ķ�������
JdbcTokenStore ����ʵ�ִ洢���Ƶ�JDBC �汾������������Ϣ���浽��ϵ�����ݿ��С� ����������乲�����ݿ����ͬһ���������ж��ʵ��������Ȩ����������Դ�������ж���������ô����ʹ��JDBC��ʽ�洢���ơ� ʹ��JdbcTokenStore ��ʱ����Ҫ��spring-jdbc���jar����ӵ����̵ı���·���С�
JSON��ҳ���ƣ�JWT�����Լ�������������Ȩ���ʵ����ݣ���˲���Ҫ�ں�̨�洢���ݣ������JWTһ����Ҫ���ŵ㣩�� ȱ�����㲻�ܷ���س���һ������Ȩ�����ƣ����һ�����Ǳ���Ȩ����Ч�ڽ϶̣�������Ȩ�Ĳ�����ˢ�������н��У��� ��һ��ȱ���Ǵ洢���������ݻ�Խ��Խ����Ϊ����������洢�˴������û�֤����Ϣ�� JwtTokenStore �಻��һ�������Ĵ洢�࣬��δ�־û������棩�κ����ݣ��������ڴ���������Ϣ����Ȩ��Ϣ����DefaultTokenServices����ʵ�֣��а�����ͬ���Ľ�ɫ�� JwtTokenStore���ӿڣ�������JwtAccessTokenConverter�࣬��Ȩ����������Դ����������Ҫ�ӿڵ�ʵ���ࣨ������ǿ��԰�ȫ��ʹ����ͬ�����ݲ����н��룩�� ������Ĭ�Ϸ�ʽ����ǩ������Դ������Ϊ���ܹ���֤��Щǩ��������Ҫ������Ȩ��������ͬ�ĶԳ���Կ������������Գ���Կ������������Ҫ�п���ƥ��ǩ��˽Կ�Ĺ�Կ������˽����Կ������Կ���� Ϊ��ʹ��JwtTokenStore �࣬����Ҫ�ڹ��̱���·�������spring-security-jwt���jar�����������Spring OAuth��github��Դ�����ҵ����������ߵİ汾���ǲ�һ�µģ���

Grant ����
AuthorizationEndpoint ͨ�� AuthorizationServerEndpointsConfigurer ��������֧�� 
Grant ���͡�Ĭ�������֧�����е� grant ���ͣ���������(�й���ϸ��Ϣ,������������Ϣ��ο����͹ر�)��
��������Ӱ��grant���ͣ�
     authenticationManager���������豻ע��һ��authenticationManager������
     authorizationCodeServices��Ϊ�������֤�������趨������Ȩ�������(org.springframework.security.oauth2.provider.code.AuthorizationCodeServicesʵ��).
     implicitGrantService������ʽ�������״̬��
     tokenGranter:TokenGranter(��ȫ�ƿص�����ͺ����������������)?��XML grant���Ͱ���authorization-server����Ԫ�ء�

	
���ö˵��URL
AuthorizationServerEndpointsConfigurer��һ��pathMapping()�������÷���������������
defaultPath Ĭ�ϵĶ˵�URL
customPath �Զ����URL 
����Լ��ṩ��URL·����/oauth/authorize����Ȩ�ˣ���/oauth/token (���ƶ�)��/oauth/confirm_access (�û�����ȷ����Ȩ������)������/oauth/error (�û�������Ȩ��������Ȩ���������)��
ע�⣺��Ȩ��/oauth/authorize������������Ӱ�䣩Ӧ������Spring Security�����ģ�������ֻ�ܱ�����Ȩ���û����ʡ����ƶ�Ĭ����ͨ��ʹ��֧��ʹ��HTTP���������֤�ͻ��������ܵ�ע��@Configuration����Spring Oauth�����ģ�������ʹ��XML�ļ��ģ�������������������������Ǻ���ȷ�ģ���
ʹ��XML��<authorization-server/>Ԫ�ؿ���ʹ��һЩ�������ﵽ�ı�Ĭ�ϵĶ˵�URL��

�Զ��������
��Ȩ�������ϴ�����ʹ�ñ�׼�� Spring MVC ����,�� @ExceptionHandler �˵㱾��ķ������û��������ṩһ�� WebResponseExceptionTranslator �˵㱾��,��õİ취�Ǹı���Ӧ�����ݶ��������ǳ��ֵķ�ʽ���쳣�ĳ��ִ��� HttpMesssageConverters (���������ӵ�MVC��������)���ƵĶ˵��OAuth�Ĵ�����ͼ(/ OAuth /error)����Ȩ�˵㡣�ṩһ��whitelabel����˵�,�����û�������Ҫ�ṩһ���Զ����ʵ��(����,�����һ�� @Controller����������ӳ���� @RequestMapping(��/ oauth /error��))��

������Դ������
��Դ�����������ܺ���Ȩ����������һ��������Ӧ�ó�����ͬһ̨�����ϣ��ṩ��OAuth2 ���Ʊ�������Դ�� Spring OAuth�ṩһ��Spring Security��Ȩ����������ʵ�ֱ�����Դ�Ĺ��ܡ���@Configuration���У������ʹ��@EnableResourceServer������/�رչ�������ʹ��ResourceServerConfigurer���������� �����ǿ����õ����ԣ�
tokenServices���������Ʒ����ʵ�壨ResourceServerTokenServices���ʵ������
resourceId����ԴID����ѡ�ģ��������ã������Ϊ�գ���Ȩ�����������������֤����
@EnableResourceServerע���һ�� OAuth2AuthenticationProcessingFilter ���͹�������ӵ�Spring Security �������С�
�� XML�У���һ��<resource-server/>Ԫ�أ�����һ��id���� �C ����servlet��������bean id����������Щ���Ա���ӵ�Spring Security���С�

����OAuth-Aware���ʽ������

�������Ҫʹ��Spring Security��ʹ�ñ��ʽ�������÷��ʿ��Ƶ��ŵ㡣 ���ʽ�������� @EnableResourceServer��������Ĭ�Ϸ�ʽ����ע�ᡣ ���ʽ����#oauth2.clientHasRole,#oauth2.clientHasAnyRole, �� #oath2.denyClient����Щ�����ṩ����oauth�ͻ��˽�ɫ�ķ��ʿ��ƣ���ϸ�б��OAuth2SecurityExpressionMethods���� ��XML�У��������<http/> ��ȫ���ýڵ���ʹ��expression-handlerԪ��ע��һ��oauth-aware���ʽ��������
OAuth 2.0 �ͻ���

OAuth 2.0 �ͻ��˿����� OAuth 2.0��������������������Դ�ķ���Ȩ�ޡ� ���ð�����������ܱ�����Դ����Ȩ�޷�����Դ���û�֮������ӡ� �ͻ���Ҳ��Ҫʵ�ִ洢�û�����Ȩ����ͷ������ƵĹ��ܡ�


�ܱ�������Դ�����ΪԶ����Դ������ʹ��OAuth2ProtectedResourceDetails���͵�ʵ��bean���塣 һ���ܱ�������Դ���������ԣ�
id����Դid�������ڿͻ���������Դ��ʱ��ʹ�ã���OAuthЭ��������δ���õ�����Ҳ������bean��id��
clientId��OAuth�ͻ���id��OAuth�ṩ���������id��ʶ��ͻ��ˡ�
clientSecret������Դ�йص����ܡ�Ĭ������£���ֵ��Ϊ�ա�
accessTokenUri���ṩ���ʿ����OAuth�ṩ���ն˵�ͳһ��Դ��ʶ����URI����
scope���Զ��ŷָ����ַ����б���ʶ�ɷ�����Դ�ķ�Χ��Ĭ������£���ֵΪ�ա�
clientAuthenticationScheme�� �ͻ��˶Է��ʵ������ն���Ȩʱʹ�õĻ��ơ� ����ֵ�� "http_basic" �� "form"�� Ĭ��ֵ�� "http_basic"�� ��OAuth 2 �����ĵ�2.1�ڡ�
��ͬ����Ȩ�����в�ͬ��ʵ��OAuth2ProtectedResourceDetails ������client_credentials��Ȩ���ͣ�ʹ��ClientCredentialsResource ���ķ�ʽ��������Ҫ�����û������֤����Ȩ���ͣ�����һ�����ԣ�
userAuthorizationUri�� �û�������Դ��Ҫ�����֤ʱ��תҳ���URI�� ע������ֶβ��Ǳ���ģ��������ڱ�֧�ֵ�OAuth 2�������ļ����͡�
��XML�У�����ʹ��<resource/>Ԫ�ش���һ��OAuth2ProtectedResourceDetails���͵�ʵ��bean�� ���������ᵽ�����е����ԡ�

ʹ��@EnableOAuth2Client��OAuth2.0�Ŀͻ��˵����ñȽϼ򵥡���ҪҪ���������飺
����һ������bean(��oauth2ClientContextFilter)���洢��ǰ������������ġ��������������Ҫ�������ڼ���Ȩ����������ض����λ�ú�OAuth����֤��url��
�������������д���һ��AccessTokenRequest���͵�bean��������͵�bean�����ڸ����û��ĳ�ͻ�б�ʶ����ʶ�𣨻���ʽ�ģ�����Ȩ�ͻ��˱�����Ȩ״̬��
�����������Ҫ�ܹ����ӵ�Ӧ�ã����磬ʹ��Servlet��ʼ���������web.xml�����ļ����� һ����DelegatingFilterProxy��ͬ���ƵĴ�����


��һ��OAuth2RestTemplate��AccessTokenRequest��������ʹ�ã�
@Autowired
private OAuth2ClientContext oauth2Context;
 
@Bean
public OAuth2RestTemplate sparklrRestTemplate() {
    return new OAuth2RestTemplate(sparklr(), oauth2Context);
}
OAuth2ClientContext������Session���������б��ֲ�ͬ�û���ͬ��״̬�����û��������ܣ�����Ҫ�����Լ��ķ���ǿ�Ϲ����Ч�����ݽṹ��ӳ�䲻���û����������������໥�����OAuth2ClientContextʵ�����Ӹ����û���
��XML�ļ��У���һ������id���Ե�<client/>��ǩ���ڱ�ʾservlet��Filter��bean id���������ӳ���һ����DelegatingFilterProxy����ͬ���Ƶ�@Configurationע�⡣


һ�������Ѿ��ṩ�����е���Դ����������ʱ����������Է�����Щ��Դ������ķ�����Щ��Դ��ͨ��ʹ����Spring3���ᵽ��RestTemplate��Spring Security OAuth�Ѿ��ṩ��һ����չ��RestTemplate��ֻ��Ҫ�ṩһ��OAuth2ProtectedResourceDetails��ʵ����ʹ������user-tokens(��Ȩ��������)��Ӧ�ÿ���ʹ��@EnableOAuth2Client����(��XML�ȼ�< oauth:rest-template / >),�����һЩ����ͻỰ�����������Ķ���,Ҫ��ͬ���û�������ʱ��������ͻ��
�ͻ��˳־û���������

�ͻ��˲���Ҫ�־û�����,���������Ժܺõ��û�����Ҫ��׼һ���µ����Ƹ�����ÿ�����������ͻ���Ӧ�ó���ClientTokenServices�ӿڶ�������Ĳ�������OAuth 2.0Ϊ�ض��û����ơ��ṩһ��JDBCʵ��,���������ϲ���Ļ������ʵ���Լ��ķ����Դ洢�ķ������Ƴ־����ݿ����ص���֤ʵ�����������ʹ�ô˹���,����Ҫ�ṩһ��ר������TokenProvider theOAuth2RestTemplate��

@Bean
@Scope(value = "session", proxyMode = ScopedProxyMode.INTERFACES)
public OAuth2RestOperations restTemplate() {
    OAuth2RestTemplate template = new OAuth2RestTemplate(resource(), new DefaultOAuth2ClientContext(accessTokenRequest));
    AccessTokenProviderChain provider = new AccessTokenProviderChain(Arrays.asList(new AuthorizationCodeAccessTokenProvider()));
    provider.setClientTokenServices(clientTokenServices());
    return template;
}


Knowvin
Knowvin
������ 9����ǰ
0�˶�
�� ����Ĳ���Ŷ!
Ϊ�ⲿ OAuth2 �ṩ�߶��ƿͻ���

һЩ�ⲿOAuth2�ṩ��(��Facebook)����ȫʵ����ȷ�淶,��������ֻ������һ���ɰ汾��Spring Security OAuth�Ĺ淶�������Ŀͻ���Ӧ�ó���ʹ����Щ��Ӧ�̿�����Ҫ��Ӧ�ͻ��˻�����ʩ�ĸ������֡�
ʹ��Facebook��Ϊһ������,��һ��Facebook����tonr2Ӧ�ó���(����Ҫ��������������Լ���,��Ч��,�ͻ���id������,���Ǻ�����������Facebook��վ��)��
Facebook��Ӧ����Ҳ����һ����һ�µġ���ʧЧʱ���JSONʵ��(����ʹ�õ��ڶ�����expires_in),�������������Ӧ�ó�����ʹ��ʧЧʱ���㽫���ò�ʹ��һ���Զ���OAuth2SerializationService�ֶ����롣


```