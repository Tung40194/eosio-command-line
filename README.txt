1. EOISO.MSIG

cleos push action eosio.token transfer '{"from": "tungpham", "to": "donocamp", "quantity": "1.0000 CAT", "memo": ""}' -p tungpham
---> OK    

cleos multisig propose p1 '[{"actor": "donocamp", "permission": "active"}]' '[{"actor": “donocamp", "permission": "active"}]' eosio.token transfer '{"from": "tungpham", "to": "donocamp", "quantity": "1.0000 CAT", "memo": ""}' -p tungpham
cleos multisig approve tungpham p1 '{"actor": "donocamp", "permission": "active"}' -p donocamp  
cleos multisig exec tungpham p1 -p tungpham
---> NOT OK

cleos multisig propose p1 '[{"actor": "donocamp", "permission": "active"}]' '[{"actor": "donocamp", "permission": "active"}]' eosio.token transfer '{"from": "donocamp", "to": "tungpham", "quantity": "1.0000 CAT", "memo": ""}' -p tungpham
cleos multisig approve tungpham p1 '{"actor": "donocamp", "permission": "active"}' -p donocamp  
cleos multisig exec tungpham p1 -p tungpham
---> OK


=> Proposer can never be the source of the proposed-transaction
    - Mainly because it doesn't make any sense for proposer to "grant itself permission"
