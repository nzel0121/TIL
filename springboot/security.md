H2 데이터베이스 콘솔 url("/h2-console/*") 요청에 대한 허용
CSRF 중지
X-Frame-Options in Spring Security 중지

http.authorizeRequests().antMatchers("/h2-console/*").permitAll()

http.csrf().disable()

http.headers().frameOptions().disable()


.csrf().requireCsrfProtectionMatcher(new AntPathRequestMatcher("!/h2-console/**")) .and().headers().addHeaderWriter(new StaticHeadersWriter("X-Content-Security-Policy","script-src 'self'")).frameOptions().disable()

.antMatchers("/", "/me", "/h2-console/**", "/login/**", "/js/**", "/css/**", "/image/**", "/fonts/**", "/favicon.ico").permitAll()
                .and().headers().frameOptions().sameOrigin()
                .and().csrf().disable()