selec t into 需要判断是否取到了相应的记录， EXCEPTION 报错
```c++
BEGIN
    SELECT DISTINCT t.counterparty_no,
    	   t.counterparty_abbr
    INTO   v_counterparty_no,
    	   v_counterparty_abbr
    FROM   clear.tc_counterparty t
    JOIN   clear.tc_foreign_inquire_match t1
    ON     t1.trade_date     = TRIM(i_trade_date)
    AND    t1.seq_no         = TRIM(i_seq_no)
    AND    t1.fn_flag        = pc.cn_fnf_near
    AND    t.counterparty_no = t1.trade_party; 

EXCEPTION
    WHEN no_data_found THEN
    o_errcode := '0100201603';
    o_errmsg  := '获取交易对手方失败! 试算放行失败!';
    GOTO l_exit;  
END;
```

