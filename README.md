# app-data

여러 앱이 배포 없이 받아 쓰는 공개 데이터 저장소.
앱은 `raw.githubusercontent.com` 주소로 파일을 받으므로 **주소가 곧 약속**이다.

```
https://raw.githubusercontent.com/woong20123/app-data/main/<앱>/<버전>/<파일>
```

## 규칙

- 저장소 이름 · 기본 브랜치(`main`) · 폴더 이름을 바꾸거나 지우지 않는다. 바꾸면 이미 깔린 앱이 갱신을 못 받는다.
- 형식이 호환되지 않게 바뀌면 기존 폴더를 고치지 말고 다음 버전 폴더(`v2` …)를 새로 만든다.
  옛 버전 앱이 남아 있는 동안은 이전 버전 폴더도 함께 갱신한다.
- 공개 저장소다. 비밀번호 · API 키 · 세션 · 쿠키 · 서명 키는 절대 넣지 않는다.
- force push 하지 않는다(다른 앱 데이터까지 덮어쓸 수 있다).
- 파일은 UTF-8 JSON. raw 주소는 몇 분 캐시되므로 바로 반영되지 않을 수 있다.

## 앱별 데이터

### forestsearch (휴양림 빈자리, Android)

| 파일 | 내용 | 만드는 곳 |
|---|---|---|
| `forestsearch/v1/forests.json` | 지역(숲나들e `srchSido`) → 휴양림 이름(`srchInstt` 글자 그대로) | `Study/AIMake/ForestSearch/scripts/update_forests.py` |
| `forestsearch/v2/prices.json` | 숙소 객실 · 야영장 자리 가격(비수기/성수기 × 평일/주말, JUN-8). 요금 묶음은 `prices`에 한 번만, 휴양림마다 `[요금 번호, 이름…]` | `Study/AIMake/ForestSearch/scripts/update_prices.py` |
| `forestsearch/v1/prices.json` | 예전 형식(숙소만, 객실마다 요금). 더 만들지 않음 | — |
| `forestsearch/privacy/index.html` | 개인정보처리방침(GitHub Pages로 공개, Play 스토어에 이 주소를 등록함: https://woong20123.github.io/app-data/forestsearch/privacy/) | `Study/AIMake/ForestSearch/docs/privacy-policy.html` |

- `forests.json`은 앱에 넣는 `app/src/main/assets/forests.json`과 같은 내용이다.
  `updated`(목록이 바뀐 날) · `checked`(사이트에서 확인한 날)로 앱이 더 새것을 고른다.
- 한 달에 한 번쯤 스크립트로 다시 만들어 커밋 · push한다.
