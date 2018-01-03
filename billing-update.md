```bash
docker exec -it shotty bash
```

```bash
cd /home/backend/utils/ && \
monit stop backend-sknt && \
monit stop backend-brownie && \
monit stop backend && \
./update-billing && \
monit start backend && \
monit start backend-sknt && \
monit start backend-brownie
```

```bash
recli "r.db('sb_generic').table('settings').get('skynet').update({'flexible': true})"
```
