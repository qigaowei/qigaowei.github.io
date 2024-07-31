```java
import feign.Client;
import feign.Feign;
import org.apache.http.conn.ssl.NoopHostnameVerifier;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

import javax.net.ssl.*;

/**
 * Feign配置，使其支持https
 */
@Configuration
public class FeignConfiguration {

    @Bean
    public Feign.Builder feignBuilder() {
        final Client trustSSLSockets = client();
        return Feign.builder().client(trustSSLSockets);
    }

    public static SSLSocketFactory feignTrustingSSLSocketFactory = null;

    @Bean
    public Client client() {
        if(feignTrustingSSLSocketFactory==null){
            try {
                feignTrustingSSLSocketFactory = getFeignTrustingSSLSocketFactory();
            } catch (Exception e) {
                e.printStackTrace();
            }
        }
        Client client= new Client.Default(feignTrustingSSLSocketFactory, new NoopHostnameVerifier());
        return client;
    }

    public static SSLSocketFactory getFeignTrustingSSLSocketFactory() throws Exception {
        javax.net.ssl.TrustManager[] trustAllCerts = new javax.net.ssl.TrustManager[1];
        javax.net.ssl.TrustManager tm = new miTM();
        trustAllCerts[0] = tm;
        javax.net.ssl.SSLContext sc = javax.net.ssl.SSLContext.getInstance("SSL");
        sc.init(null, trustAllCerts, null);
        return sc.getSocketFactory();
    }
    static class miTM implements javax.net.ssl.TrustManager, javax.net.ssl.X509TrustManager {
        public java.security.cert.X509Certificate[] getAcceptedIssuers() {
            return null;
        }

        public boolean isServerTrusted(java.security.cert.X509Certificate[] certs) {
            return true;
        }

        public boolean isClientTrusted(java.security.cert.X509Certificate[] certs) {
            return true;
        }

        public void checkServerTrusted(java.security.cert.X509Certificate[] certs, String authType)
                throws java.security.cert.CertificateException {
            return;
        }

        public void checkClientTrusted(java.security.cert.X509Certificate[] certs, String authType)
                throws java.security.cert.CertificateException {
            return;
        }
    }

}
```
```xml
  <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-openfeign</artifactId>
        </dependency>
<dependency>
            <groupId>org.apache.httpcomponents</groupId>
            <artifactId>httpclient</artifactId>
            <version>4.5.13</version>
        </dependency>
```
```java
@Component
@FeignClient(name = "NgfwApiFeign", url = "https://fakeAIMASKurl", configuration = FeignConfiguration.class)
public interface NgfwApiFeign {
```