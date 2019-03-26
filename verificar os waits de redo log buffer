set lines 155
set pages 500
 
column "col1" heading "Evento" format a50 
column "col2" heading "Número Esperas" format 99,999,999,999
column "col3" heading "Média ESPERA (S)" format 99,999.90
 
select
 event                  "col1" ,
 sum(total_waits)       "col2" ,  
 avg(average_wait)/100   "col3"
from
 v$system_event
where
 average_wait > 0
and event in
(
 'Log archive I/O','log buffer space','log file sync','log file parallel write','log file sequential read','log file single write'
 ,'Log file init write','log file switch (archiving needed)','log file switch (checkpoint incomplete)','log file switch (clearing log file)'
    ,'log file switch completion','log file switch (private strand flush incomplete)','log switch/archive','log write(even)','log write(odd)'
)
group by event
order by 3 desc;
