## Implementasyon Detayları

* Car ve Manufacture arraylari id kullanılarak joinlendi ve gerekli columnlar select sorgusuna dahil edildi. 
* Purchase arrayi içerisindeki date değeri 3 saat artırılarak sorguya dahil edildi.

## Code

```SQL
SELECT
  name,
  c.id as car_id,
  c.model as car_model,
  m.year as manufacture_year,
  ARRAY(select as struct p.* replace(timestamp_add(p.date, interval 3 hour) as date) 
  FROM unnest(purchase) as p) as purchase 
FROM 
  ahmet_lekesiz.semi_structured_hw
JOIN UNNEST(CAR) as c
JOIN UNNEST(MANUFACTURE) as m
ON c.id = m.id
```
