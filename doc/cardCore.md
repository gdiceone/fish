##卡卷接口

###引用jar包
````
<dependency>
	<groupId>org.doyutu</groupId>
	<artifactId>do-card</artifactId>
	<version>0.0.1-SNAPSHOT</version>
</dependency>
````

###接口 CardCoreOperatorService

#### 生成模板卡卷
````
/**
     * 生成模板卡券
     * @param dto
     * @return      卡券池编号
     */
String generatorTemplate(CardCoreTemplateDTO dto);
````

#### 调整卡卷总账
````
/**
     * 调整卡券总账
     * @param depositAmount     调整充值大小，可减少
     * @param coin              币种
     * @param operator          操作人
     * @param memo              备注
     */
void generalDeposit(BigDecimal depositAmount, String coin, String operator, String memo);
````

#### 使用卡卷
````
 /**
     * 使用卡券
     * @param userId            userId
     * @param poolDetailNo      卡券detailNo
     * @param projectType       项目类型
     * @param coin              币种
     * @param tradeAmount       交易金额
     * @return                  卡券新订单实际需要支付的金额（可以为0）
     */
    BigDecimal applyCard(String userId, String poolDetailNo, String projectType, String coin, BigDecimal tradeAmount, CardUserBindFunction cardUserBind);

````

#### 发放卡卷
````
/**
     * 发放卡券
     * @param dto
     */
    void grantCard(CardCoreGrantDTO dto);
````

#### GXB发放卡卷
````
 /**
     * GXB发放卡券
     * @param dto
     * @param notifyJsonDTO
     */
    void grantGxbCard(CardCoreActivateDTO dto, CardCoreActivateNotifyJsonDTO notifyJsonDTO, String userId, Integer status);
````

#### 改变过期卡卷
````
/**
     * 改变过期卡券
     */
    void changeExpiredCard();
````

#### 第三方绑定用户卡卷账户
````
 /**
     * 第三方绑定用户卡券账户
     * @param uid           第三方UID
     * @param applyFrom     来源
     */
    void changeNewCard(String key, String uid, CardCoreApplyFromEnum applyFrom, CardUserBindFunction cardUserBindFunction);
````

#### 第三方绑定用户卡卷账户
````
/**
     * 第三方绑定用户卡券账户
     * @param uid           第三方UID
     * @param applyFrom     来源
     */
    void changeNewCard(String uid, CardCoreApplyFromEnum applyFrom, CardUserBindFunction cardUserBindFunction);
````    


###接口 CardCoreQueryService

#### 用户卡卷包查询
````
  /**
     * 用户卡券包查询
     *
     * @param userId
     * @param available    null:所有类型，true：可用，false：失效
     * @return
     */
    PageInfo<CardcoreUserUseCardVO> getUserUseCard(String userId,
                                                   int pageNum, int pageSize,
                                                   Boolean available, CardCoinFunction cardCoinFunction);
````

#### 获取可用卡卷
````
/**
     *
     * @param userId
     * @param coinConstants
     * @param projectType
     * @return
     */
    List<CardCoreGetAvailableCardDTO> getAvailableCard(String userId, String coinConstants, String projectType);
````