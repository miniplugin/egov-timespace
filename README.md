## 이전에 작업한 전자정부표준프레임웍(이하 egov로 표기)<br> 기반 CMS 에서 연동 SW 점검 1.
***
전자정부 표준프레임워크 라이선스는 Apache 2.0 라이선스를 따릅니다.부트스트랩/AdminLTE/기타등등<br>
표준프레임워크 내에서 사용된 외부 오픈소스의 경우 원 오픈소스의 라이선스 정책을 유지합니다.
[라이센스 보기](https://www.egovframe.go.kr/EgovLicense.jsp)
***
>작업일자(아래): 20200221(예정)
### 연동 SW 점검 1. /egovSampleList.do와 삭제는 정상인데, 등록/수정에서 문제가 있음.
- 확인예정

>작업일자(아래): 20200220
### 연동 SW 점검 1. 표준프레임웍으로 구성된 프로젝트(게시판)을 CMS솔루션에 적용 특이사항.
- 결과확인 URL: http://도메인/egovSampleList.do
'''xml
context-datasource.xml파일에서 아래 내용 추가
<!-- hsql -->
<jdbc:embedded-database id="dataSource-hsql" type="HSQL">
	<jdbc:script location= "classpath:/db/timespace_hsql.sql"/>
	<jdbc:script location= "classpath:/db/sampledb.sql"/><!-- 이부분 추가 -->
</jdbc:embedded-database>
sampledb.sql 내용 중에서 IDS는 기존값과 중복되기 때문에 제거
CREATE MEMORY TABLE IDS(TABLE_NAME VARCHAR(16) NOT NULL PRIMARY KEY,NEXT_ID DECIMAL(30) NOT NULL)
INSERT INTO IDS VALUES('SAMPLE',115)
'''
ScreenShot<br>
![ex_screenshot](./git_img/20200221.jpg)
![ex_screenshot](./git_img/20200221_2.jpg)

### Egov시작 클래스명 변경.
- egovframework.rte. 유지.
- egovframework.com. , egovframework.let. 일괄변경 framework.com. framework.let.   