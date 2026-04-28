```js
 {{if val.orderVoidFlag == '1'}}
	     <span style="text-decoration: line-through;">{{val.orderShowName || ''}}</span>
	  {{else}}
	     {{val.orderShowName || ''}}
	  {{/if}}
```