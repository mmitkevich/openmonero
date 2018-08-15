### Логика поиска транзакций

инкапсулирована в классе `OutputInputIdentification` 

[OutputInputIdentification:11](https://github.com/moneroexamples/openmonero/blob/master/src/OutputInputIdentification.cpp#L11)

Класс абстрагирует операцию поиска "своих" инпутов и аутпутов для конкретной транзакции `tx` и конкретного `viewkey`

### Конструктор

```c++
OutputInputIdentification::OutputInputIdentification(
    const address_parse_info* _a, // TODO: это публичный спенд-ключ?
    const secret_key* viewkey,
    const transaction* tx)
    : total_received {0}, mixin_no {0}
{
// берем P транзакции из полей extra
tx_pub_key=get_tx_pub_key_from_received_outs(tx) 
if(!generate_key_derivation(tx_pub_key, viewkey, derivation)) FAIL();
}
```
В соответствии с WP для идентификации инпутов достаточно пары

`(a,B)`==`(private view key, public spend key)`

- TODO: что такое a? публичный ключ `B`?
- TODO: viewkey это приватный ключ `a`?
- TODO: что конкретно проверяет generate_key_derivation?


###  identify_inputs

Ищем входы.
```c++
identify_inputs(
    vector<  pair<
                public_key,     // TODO: публичный ключ чей?
                uint64_t>>&     // TODO: что за индекс?
        known_outputs_keys)
``` 
- TODO: что такое kown_outputs_keys?





