# hello-world
my first hello-world repository
SELECT SUBSTRING(KOSTL, 2, 1) + '00' AS KOSTL,
       ROUND(SUM(ISNULL(DataDate_WORK, 0) + ISNULL(WORK_TIME, 0) +
                 ISNULL(DATADATE_OT, 0) + ISNULL(OVER_TIME, 0) +
                 ISNULL(CONSUME_TIME, 0) + ISNULL(HOUR_WORK, 0) +
                 ISNULL(HOUR_OT, 0)) /
             +SUM(ISNULL(DirectA, 0) - ISNULL(BOFF, 0) + ISNULL(BOT, 0)),
             4) AS TTRT
  From View_For_A800_4_DataDate
 WHERE (Year = '2017')
   AND (Month = '05')
 GROUP BY SUBSTRING(KOSTL, 2, 1)
Union
SELECT SUBSTRING(KOSTL, 2, 2) + '0' AS KOSTL,
       ROUND(SUM(ISNULL(DataDate_WORK, 0) + ISNULL(WORK_TIME, 0) +
                 ISNULL(DATADATE_OT, 0) + ISNULL(OVER_TIME, 0) +
                 ISNULL(CONSUME_TIME, 0) + ISNULL(HOUR_WORK, 0) +
                 ISNULL(HOUR_OT, 0)) /
             SUM(ISNULL(DirectA, 0) - ISNULL(BOFF, 0) + ISNULL(BOT, 0)),
             4) AS TTRT
  From View_For_A800_4_DataDate
 WHERE (Year = '2017')
   AND (Month = '05')
 GROUP BY SUBSTRING(KOSTL, 2, 2)
Union
SELECT SUBSTRING(KOSTL, 2, 3) AS KOSTL,
       ROUND(SUM(ISNULL(DataDate_WORK, 0) + ISNULL(WORK_TIME, 0) +
                 ISNULL(DATADATE_OT, 0) + ISNULL(OVER_TIME, 0) +
                 ISNULL(CONSUME_TIME, 0) + ISNULL(HOUR_WORK, 0) +
                 ISNULL(HOUR_OT, 0)) /
             SUM(ISNULL(DirectA, 0) - ISNULL(BOFF, 0) + ISNULL(BOT, 0)),
             4) AS TTRT
  From View_For_A800_4_DataDate
 WHERE (Year = '2017')
   AND (Month = '05')
   AND SUBSTRING(KOSTL, 4, 1) <> '0'
 GROUP BY SUBSTRING(KOSTL, 2, 3)
 ORDER BY KOSTL
