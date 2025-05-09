# 1. 스프링 시큐리티(Spring Security)란?
Spring Framework 기반의 애플리케이션에서 인증(Authentication)과 권한 부여(Authorization)를 담당하는 보안 프레임워크.

웹 보안, 메서드 보안 등을 강력하게 지원하며, 유연하게 커스터마이징이 가능한 것이 큰 장점.

# 2. 스프링 시큐리티의 핵심 개념들

## 🔐 1. 인증(Authentication)
사용자가 누구인지 확인하는 과정.

예) 사용자가 로그인 폼에 아이디/비밀번호를 입력하면, 이 정보를 기반으로 사용자를 확인.

### 주요 컴포넌트

Authentication: 인증 정보를 담는 객체 (사용자 이름, 비밀번호, 권한 등)

AuthenticationManager: 인증 처리를 담당

UserDetailsService: 사용자 정보를 로드 (DB에서 유저 정보 가져오기)

UserDetails: 사용자 정보를 담는 인터페이스 구현체

## 🛡 2. 인가/권한 부여(Authorization)
인증된 사용자가 무엇을 할 수 있는지 결정하는 과정.

예) 관리자는 /admin에 접근 가능하지만 일반 사용자는 접근 불가.

### 주요 방식

URL 기반 권한 부여 (http.authorizeRequests())

메서드 수준 보안 (@PreAuthorize, @Secured)

## ⚙️ 3. 주요 설정 클래스와 구성 요소
스프링 시큐리티는 일반적으로 SecurityConfig 같은 설정 클래스를 통해 구성.

<pre>
  <code>
    @Configuration
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .authorizeRequests()
                .antMatchers("/admin/**").hasRole("ADMIN")
                .anyRequest().authenticated()
            .and()
                .formLogin()
            .and()
                .logout();
    }

    @Override
    protected void configure(AuthenticationManagerBuilder auth) throws Exception {
        auth.inMemoryAuthentication()
            .withUser("user").password("{noop}password").roles("USER");
    }
}
  </code>
</pre>

※ Spring Security 6.0 이상에서는 WebSecurityConfigurerAdapter는 deprecated 되었고, SecurityFilterChain 방식으로 전환.

## 🧱 4. 필터 기반 구조
스프링 시큐리티는 서블릿 필터 체인을 기반으로 동작.

### 주요 필터:

UsernamePasswordAuthenticationFilter: 로그인 요청 처리

SecurityContextPersistenceFilter: 보안 컨텍스트 유지

ExceptionTranslationFilter: 예외 처리

## 🔄 5. 커스터마이징
사용자 정의 로그인 페이지

JWT 기반 인증

OAuth2 소셜 로그인

API 보안 설정 (CORS, CSRF, Stateless 설정 등)
