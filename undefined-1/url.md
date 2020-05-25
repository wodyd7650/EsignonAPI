# 문서 다운로드 URL 생성

회사 ID 와 문서의 ID 를 통하여 문서를 다운로드 할 수 있는 URL 을 가져옵니다.

주의 \) 문서 보안을 위해 Client\_id 를 사용합니다. id 값이 노출 될 경우 URL이 노출 될 수 있습니다.

생성된 URL은 5분간 유지됩니다.

{% api-method method="post" host="https://docs.esignon.net" path="/workflow/download" %}
{% api-method-summary %}
workflowdownload
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=false %}
application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="wfuid" type="string" required=true %}
완료 된 문서의 ID 값
{% endapi-method-parameter %}

{% api-method-parameter name="client\_id" type="string" required=true %}
esignon 에서 발급받은 ID 
{% endapi-method-parameter %}

{% api-method-parameter name="comp\_id" type="string" required=true %}
회사 ID
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
	"header":{
	"response_code": "/workflow/download",
	"result_code": "00",
	"result_msg": "Success",
	"session_id": ""
	},
	"body":{
	"result_url": "{다운로드 URL}",
	"wfname": "{문서 이름}"
	}
}

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

Example\) Request Body

```text
{
	"comp_id": "{회사 ID}",
	"wfuid": "{완료 된 문서의 ID 값}",
  "client_id":"{발급받은 클라이언트 ID}"
}
```

Example\) Respnse Body

완료 된 문서가 아닐 경우 아래와 같은 메세지 출력

```text
<script type="text/javaScript">
alert("workflow is not Complete");
window.close();
</script>
```

