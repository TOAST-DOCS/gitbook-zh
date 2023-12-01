## Search > Address Search > API v1.0 Guide

Address Search를 사용하는데 필요한 API를 설명합니다.

## 주소 검색하기

질의와 일치하는 주소 정보를 최대 100개까지 반환합니다. 검색된 주소 정보는 사용자 질의와 가장 유사한 순서로 정렬됩니다. 따라서 totalCount가 100 이상인 경우에는 사용자에게 좀 더 구체적인 주소를 질의로 입력할 것을 안내하는 것이 좋습니다.

### 요청

[URI]

| 메서드 | URI |
| --- | --- |
| GET | http://api-address.cloud.toast.com/address/v1/appkeys/{appKey}/addresses |

[요청 헤더]

이 작업은 별도의 요청 헤더를 요구하지 않습니다.

[요청 본문]

이 작업에는 요청 본문이 없습니다.

[필드]

| 이름 | 유형 | 필수 여부 | 유효 범위 | 설명 |
| --- | --- | ----- | ----- | --- |
| q | String | 필수 |  | 질의 |
| region | String |  | kr/jp | 대상 국가 코드. 지정하지 않으면 기본값은 kr |
| startRank | int |  | 1~1,000 | 몇 번째 검색 결과부터 반환할 것인지를 지정.<br>지정하지 않으면 기본값은 1. |
| returnCount | int |  | 1~100 | 몇 개의 검색 결과를 반환할 것인지를 지정.<br>지정하지 않으면 기본값은 100. |

### 응답

Address Search의 응답 유형은 요청 대상 국가의 주소체계 특징에 따라 다릅니다.

#### KR

[응답 본문]

```
{
    "header": {
        "isSuccessful": boolean,
        "resultCode": int,
        "resultMessage": String
    },
    "body": {
        "query": String,
        "totalCount": int,
        "addresses" : [
            {
                "roadAddress": String,
                "roadAddressExtra": String,
                "roadAddressEnglish": String,
                "jibunAddress": String,
                "relatedJibun": String,
                "dongCode": String,
                "roadCode": String,
                "buildingCode": String,
                "zipCode": String,
                "oldZipCode": String
            },
            ...
        ],
        "groupByState": [
            {
                "state": String,
                "count": int
            },
            ...
        ],
        "startRank": int,
        "returnCount": int
    }
}
```

[필드]

| 이름 | 유형 | 설명 |
| --- | --- | --- |
| query | String | 질의 |
| totalCount | int | 검색된 주소의 총 갯수 |
| addresses | List | 검색된 주소 목록 |
| roadAddress | String | 기본 도로명주소 |
| roadAddressExtra | String | 도로명주소의 참고 항목 |
| roadAddressEnglish | String | 영문 도로명주소 |
| jibunAddress | String | 지번 주소 |
| relatedJibun | String | 관련 지번 |
| dongCode | String | 법정동 코드 |
| roadCode | String | 도로명 코드 |
| buildingCode | String | 건물 관리 번호 |
| zipCode | String | 새 우편번호 |
| oldZipCode | String | 기존 우편번호<br>(※ 2015년 8월 1일 이후 추가/변경된 건물은 행정자치부가 기존 6자리 우편번호를 제공하지 않음. 이 경우, 필드는 '000-000'을 반환.) |
| groupByState | List | 검색된 주소 개수를 시/도 단위로 묶은 결과 목록 |
| state | String | 묶은 시/도 이름 |
| count | int | 묶은 시/도 각각의 개수 |
| startRank | int | 반환된 주소의 시작 등수 |
| returnCount | int | 반환된 주소의 총 개수. totalCount보다 작거나 같음. |

#### JP

[응답 본문]

```
{
    "header": {
        "isSuccessful": boolean,
        "resultCode": int,
        "resultMessage": String
    },
    "body": {
        "query": String,
        "totalCount": int,
        "addresses" : [
            {
                "address": String,
                "addressEnglish": String,
                "jisCode": String,
                "zipCode": String
            },
            ...
        ],
        "groupByState": [
            {
                "state": String,
                "count": int
            },
            ...
        ],
        "startRank": int,
        "returnCount": int
    }
}
```

[필드]

| 이름 | 유형 | 설명 |
| --- | --- | --- |
| query | String | 질의 |
| totalCount | int | 검색된 주소의 총 갯수 |
| addresses | List | 검색된 주소 목록 |
| address | String | 주소 |
| addressEnglish | String | 영문 주소 |
| jisCode | String | 전국 지방공공단체 코드 |
| zipCode | String | 우편번호 |
| state | String | 묶은 도도부현 이름 |
| count | int | 묶은 도도부현 각각의 개수 |
| startRank | int | 반환된 주소의 시작 등수 |
| returnCount | int | 반환된 주소의 총 개수. totalCount보다 작거나 같음. |

## 참고 사항

### 좋은 질의의 예

* 삼평동 629: 동(洞)과 번지수를 입력하면 정확한 주소를 찾을 수 있습니다.
* 성남시 대왕판교로645번길 16: 도로명과 건물번호를 입력하면 정확한 주소를 찾을 수 있습니다.
* 동천마을동문굿모닝힐5차: 건물이름만 입력하여 주소를 찾을 수 있습니다.
* 동천동 동문5차: 동(洞)과 건물이름을 함께 입력해서 검색할 수 있습니다.

### 좋지 않은 질의의 예

* 경기도 성남시 분당구 삼평동: 비교적 상세하나 번지수가 지정되지 않아, 삼평동의 모든 주소를 반환합니다.
* 대왕판교로: 건물 번호가 지정되지 않아, 해당 도로 주변의 모든 주소를 반환합니다.
* 정자동: 정자동의 모든 주소를 반환합니다.
