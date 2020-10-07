search condition - check box
```
<div class="chk_div">
    <div class="check-wrap chk_st1">
        <input type="radio" id="sSelectAll" name="statusCode" value=""
               th:checked="${#strings.isEmpty(condition.statusCode)}"/>
        <label for="sSelectAll">전체</label>
    </div>
    <div class="check-wrap chk_st1">
        <input type="radio" id="sSelect0" name="statusCode" value="REQUEST"
               th:checked="${condition.statusCode == 'REQUEST'}"/>
        <label for="sSelect0">신청</label>
    </div>
    <div class="check-wrap chk_st1">
        <input type="radio" id="sSelect1" name="statusCode" value="PROGRESS_COMPLETED"
               th:checked="${condition.statusCode == 'PROGRESS_COMPLETED'}"/>
        <label for="sSelect1">승인</label>
    </div>
    <div class="check-wrap chk_st1">
        <input type="radio" id="sSelect2" name="statusCode" value="CANCEL"
               th:checked="${condition.statusCode == 'CANCEL'}"/>
        <label for="sSelect2">거절</label>
    </div>
    <div class="check-wrap chk_st1">
        <input type="radio" id="sSelect3" name="statusCode" value="COMPLETE"
               th:checked="${condition.statusCode == 'COMPLETE'}"/>
        <label for="sSelect3">제공</label>
    </div>
</div>
```

search condition - select box
```
<select name="statusCode" id="statusCode">
    <option value="" th:selected="${condition.statusCode} == null">상태</option>
    <option th:text="신청" th:value='REQUEST'
            th:selected="${condition?.statusCode == 'REQUEST'}"></option>
    <option th:text="승인" th:value='PROGRESS_COMPLETED'
            th:selected="${condition?.statusCode == 'PROGRESS_COMPLETED'}"></option>
    <option th:text="거절" th:value='CANCEL'
            th:selected="${condition?.statusCode == 'CANCEL'}"></option>
    <option th:text="제공" th:value='COMPLETE'
            th:selected="${condition?.statusCode == 'COMPLETE'}"></option>
</select>
```
