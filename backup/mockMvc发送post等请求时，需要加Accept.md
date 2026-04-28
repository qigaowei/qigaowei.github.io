mockMvc发送post等请求时，需要加Accept， .accept(MediaType.APPLICATION_JSON)
要不返回的可能是xml
```java
mockMvc.perform(post("/api/v1/")
                        .contentType(MediaType.APPLICATION_JSON)
                        .accept(MediaType.APPLICATION_JSON)
                        .content("{}"))
                .andExpect(status().isOk())
                .andExpect(jsonPath("$.success").value(true));
```