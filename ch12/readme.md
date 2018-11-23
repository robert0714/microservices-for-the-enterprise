
# Setting Up an OAuth 2.0 Authorization Server

p.353

Using the client credentials OAuth 2.0 grant type: 

```
\>  curl -v -X POST --basic -u  10101010:11110000  \
  -H "Content-Type:application/x-www-form-urlencoded;charset=UTF-8"    \
  -k -d "grant_type=client_credentials&scope=foo"    \
 https://localhost:8443/oauth/token
```

Using the password OAuth 2.0 grant type: 

```
\>  curl -v -X POST --basic -u  10101010:11110000  \
  -H "Content-Type:application/x-www-form-urlencoded;charset=UTF-8" \
  -k -d "grant_type=password&username=peter&password=peter123&scope=foo"  \
 https://localhost:8443/oauth/token
```

p.354

```

\>  curl -k -X POST -H "Authorization: Bearer $TOKEN"    \
-H "Content-Type:application/json"   https://localhost:8443/user

\>  curl -k -X POST -H "Authorization: Bearer  d1773b12-1a3a-43eb-b362-3a2228961603"    \
  -H "Content-Type:application/json"   https://localhost:8443/user
```

#  Protecting a Microservice with OAuth 2.0
p.357

```
\>  curl -v -X POST --basic -u  10101010:11110000   \
  -H "Content-Type:application/x-www-form-urlencoded;charset=UTF-8"   \
   -k -d "grant_type=client_credentials&scope=foo" https://localhost:8443/oauth/token

\>  curl -v -X POST --basic -u  10101010:11110000  \
  -H "Content-Type:application/x-www-form-urlencoded;charset=UTF-8" \
  -k -d "grant_type=password&username=peter&password=peter123&scope=foo"  \
 https://localhost:8443/oauth/token


\>  curl -k -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE1NDI5NDA5NTgsInVzZXJfbmFtZSI6InBldGVyIiwiYXV0aG9yaXRpZXMiOlsiUk9MRV9VU0VSIl0sImp0aSI6ImFlMzllMGI3LTQ1YTEtNDJjYi04ZWI2LWFiZTEyMDJmNTg4YSIsImNsaWVudF9pZCI6IjEwMTAxMDEwIiwic2NvcGUiOlsiZm9vIl19.N2ZGMP6BBtjkxrEa5OH6l3l1CYzogB_1MEJ-dP5fRMHjojOgY1KwKPxvLWy-tUwD9KsEcfVB0LVA_61oxE6LdjKhWHE-FhOMudnYVcwgpzxPROLztYyDLFgysDenetMpKWDaWuz0px0u8wmRY5fCyCB-8c7tE3yukHFMDx2CtaRzUvivgLOJxnjzUldzX4WT2tcXILHyt4akaw6fLwTDJ0fPDwbkmkC6XPZMiGx8fyxQCbymbE9cvjGBeq2jQ97K3-qyqmCRV07RxAM9DXMSK7uMGFOjtCWf7dRrUEKegRSKxzZyfvPSrX-Yr4Z-4za4hOb_UlAz6a4HhIeV2Rfj8A"   https://localhost:9443/order/11


\>  curl -k -H "Authorization: Bearer  d1773b12-1a3a-43eb-b362-3a2228961603"   https://localhost:9443/order/11

```


# Controlling Access to a Microservice

## Scope-Based Access Control

p.363

```
\>  curl -v -X POST --basic -u  10101010:11110000   \
  -H "Content-Type:application/x-www-form-urlencoded;charset=UTF-8"   \
   -k -d "grant_type=client_credentials&scope=foo" https://localhost:8443/oauth/token


\>  curl -k -H "Authorization: Bearer  d1773b12-1a3a-43eb-b362-3a2228961603"   https://localhost:9443/order/11
```

## Role-Based Access Control

p.364

```
\>  curl -v -X POST --basic -u  10101010:11110000  \
  -H "Content-Type:application/x-www-form-urlencoded;charset=UTF-8" \
  -k -d "grant_type=password&username=peter&password=peter123&scope=foo"  \
 https://localhost:8443/oauth/token


\>  curl -k -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE1NDI5NDA5NTgsInVzZXJfbmFtZSI6InBldGVyIiwiYXV0aG9yaXRpZXMiOlsiUk9MRV9VU0VSIl0sImp0aSI6ImFlMzllMGI3LTQ1YTEtNDJjYi04ZWI2LWFiZTEyMDJmNTg4YSIsImNsaWVudF9pZCI6IjEwMTAxMDEwIiwic2NvcGUiOlsiZm9vIl19.N2ZGMP6BBtjkxrEa5OH6l3l1CYzogB_1MEJ-dP5fRMHjojOgY1KwKPxvLWy-tUwD9KsEcfVB0LVA_61oxE6LdjKhWHE-FhOMudnYVcwgpzxPROLztYyDLFgysDenetMpKWDaWuz0px0u8wmRY5fCyCB-8c7tE3yukHFMDx2CtaRzUvivgLOJxnjzUldzX4WT2tcXILHyt4akaw6fLwTDJ0fPDwbkmkC6XPZMiGx8fyxQCbymbE9cvjGBeq2jQ97K3-qyqmCRV07RxAM9DXMSK7uMGFOjtCWf7dRrUEKegRSKxzZyfvPSrX-Yr4Z-4za4hOb_UlAz6a4HhIeV2Rfj8A"   https://localhost:9443/order/11


\>  curl -k -H "Authorization: Bearer  d1773b12-1a3a-43eb-b362-3a2228961603"   https://localhost:9443/order/11

```

# Securing Service-to-Service Communication

## Service-to-Service Communication Secured with JWT

p.367

```
\>  curl -v -X POST --basic -u  10101010:11110000  \
  -H "Content-Type:application/x-www-form-urlencoded;charset=UTF-8" \
  -k -d "grant_type=password&username=peter&password=peter123&scope=foo"  \
 https://localhost:8443/oauth/token


\>  curl -k -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE1NDI5NDI0MjUsInVzZXJfbmFtZSI6InBldGVyIiwiYXV0aG9yaXRpZXMiOlsiUk9MRV9VU0VSIl0sImp0aSI6IjBjZDU3NTI0LWNjM2YtNGU3NS04YWQ4LWU2YjlmY2YyMjEwZiIsImNsaWVudF9pZCI6IjEwMTAxMDEwIiwic2NvcGUiOlsiZm9vIl19.sMpXIA8SB8iWCDrj_UyhS0nL22YUZBW7ug3frJUrQQ3P1C_LJk3CrjfovOEOpVwzZomTTd3bEbxeMVMHL2ZTT85qcHds7JcooKGeE5j_IZcGDemruQseVnjh0s-JiPHVHktzgAKw7xczse7j9CXgn9h9lljGEQl9NWuxk7DJsv0RqfEtaf6EmDuxobJv8JD7RxoZz-kOTB0q1lu5RGH5h1CQQeRIz6lUFfBdd75vCX9cW74G3r7ykLeeNYzZPGm4tRcnrXvcrU8WCHP_Be6nwzuTNdP5BjNv3HTyaZMS-YYbKHfcLmuCy2gfAZlRE1oerKz-8q3EnXcDCUL9i8936g"      \
-H "Content-Type:application/json" -d '{"customer_id":"101021","payment_method":{"card_type":"VISA","expiration":"01/22","name":"John Doe","billing_address":"201, 1st Street, San Jose, CA"},"items":[{"code":"101","qty":1},{"code":"103","qty":5}],"shipping_address":"201, 1st Street, San Jose, CA"}'   \
  https://localhost:9443/order


```
