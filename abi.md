**abi接口  管理员创建竞猜**
``` javascript
  /**
   * 创建一个竞猜
   * @param assetId 下注的资产id
   * @param minChip 每个用户下注时的最小筹码个数
   * @param maxChip 每个用户下注时的最大筹码个数
   * @param optCount 竞猜选项个数，大于2小于9
   * @param endGuess 下注截止时间，格林威治时间1970年01月01日00时00分00秒起的总秒数
   * @return 返回创建好的竞猜id
   */
    function newguess(uint256 assetId, uint256 minChip, uint256 maxChip, uint optCount, uint256 endGuess) public returns (uint64 gid)
```

**abi接口  用户下注**
``` javascript
  /**
   * 下注竞猜，用户调用此接口并转账资产给合约，资产类型和数量为newguess创建时指定
   * @param gid newguess创建竞猜时返回的id
   * @param opt 下注第几个选项，选项序号从0开始
   * @return 无
   */
    function guess(uint64 gid, uint opt) payable
```

**abi接口  管理员开奖**
``` javascript
  /**
   * 开奖
   * @param gid newguess创建竞猜时返回的id
   * @param opt 中奖选项，选项序号从0开始
   * @return 无
   */
    function endguess(uint64 gid, uint opt) public
```

**abi接口  管理员发放奖励**
``` javascript
  /**
   * 发放奖励。因怕引起失败一次性转账5个账户，发奖后台程序独立运行。
   * @param gid newguess创建竞猜时返回的id
   * @param winer 获奖者，一次最多处理5个获奖者
   * @return 无
   */
    function reward(uint64 gid, address[5] winer) public
```

**abi接口  失败者获得矿**
``` javascript
  /**
   * 给失败者发矿。因怕引起失败一次性转账5个账户，发矿由后台程序独立运行。
   * @param gid newguess创建竞猜时返回的id
   * @param loser 获奖者，一次最多处理5个获奖者
   * @return 无
   */
    function mining(uint64 gid, uint opt, address[5] loser) public
```

**abi接口  设置管理员**
``` javascript
  /**
   * 设置合约管理员，目前只支持一个管理员。
   * @param manager 管理员
   * @return 无
   */
    function setmgr(address manager)
```