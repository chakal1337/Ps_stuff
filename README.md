# Ps_stuff
useful things for aqw private servers

Queries:
 For no free coins / gold 

  Monsters:
   
    update items set cost=0 where id in (select itemid from (select * from monsters_drops) as itemid)

  Quests:
    
    update items set cost=0 where id in (select itemid from (select * from quests_rewards) as itemid)

  Auto shops
  
    insert into shops_items(shopid,itemid,quantityremain) 
    select "999", id, 0 from items where id not in (select id from ( select * from items where staff=0) as id)
    order by rand() limit 10

  See items from specific user
  
    select * from users_items right join items on users_items.itemid = items.id where userid='56'
