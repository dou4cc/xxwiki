#部署GAE时，appid正在使用，导致部署失败

##现象：
  已经有可用的appid，假设名字为xagent  
  在XX-Net发布新版后，把xagent设置为当前工作appid，然后去部署xagent，此时会部署失败

##原因：
  部署过程，Google App Engine 需要暂停该appid的老版本工作，然后启用新版本。
  在暂停老版本后，而新版本还未启用的期间，XX-Net无法跟Google App Engine通讯，导致部署失败。

##解决方案：
  如果有多个appid，可以设置一个作为当前工作的appid，部署其他的appid，然后轮换，部署这个appid。
  如果没有，就先不填appid，系统会使用预置的appid，部署成功后，再去使用自己的appid。

##很多appid即使用又部署：
  有一定概率会成功，也有可能会遇到问题，看运气。
