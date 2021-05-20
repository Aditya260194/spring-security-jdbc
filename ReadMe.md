# spring -security-jdbc
spring boot + spring security + jdbc

1. Add h2 dependency and jdbc api dependency in pom

Configure security

2. Spring security uses AuthenticationManager to authenticate user. We can't change AuthenticationManager directly, instead we use AuthenticationManagerBuilder
   to configure AuthenticationManager.
3. We configure it using WebSecurityConfigurerAdapter and override the configure method for AuthenticationManagerBuilder.

JDBC Authentication

4. We configure it for jdbc authentication by overriding configure method.
5. We put our ddl statements in schema.sql and DMl statements in data.sql so it creates /inserts data in tables which are need for authentication.
6. By default spring-security has its own schema, we can use that or create our own.

This way spring will authenticate our users from database rather than doing in-memory authentication which we did in earlier project.

All authentication manager like JDBC and LDAP, calls loadUserByUserName() method of UserDetailsService which is Spring's own implementation.
so in return the principal returned by AuthenticationManager is basically UserDetails.
In real we are not dealing with UserDetailsService here, but internally user are picked from database using loadUserByUsername() method.

If we want to create our own implementation of AuthenticationManager, we have to create our own UserDetailsService.


