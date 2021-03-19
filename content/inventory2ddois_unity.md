---
title: 'Sistema de Inventário 2D - Parte 2'
---
## 🏵️ Primeiro passo ##

Crie um `C# Script` chamado `Slots`.

# Bibliotecas #
```
/*bibliotecas aqui*/
```

# Variáveis iniciais #
```
    private Inventory inventory; // *warning tip
    public int i;
```
#
<Warning>* A classe dessa variável deve conter o MESMO nome do script criado anteriormente.
</Warning>

# Código

```
    void Start()
    {
        inventory = GameObject.FindGameObjectWithTag("Player").GetComponent<invetariozao>();

    } 
```
#
```
    private void Update()
    {
        if (transform.childCount <= 0)
        {
            inventory.isFull[i] = false;
        }
    }
```
#
```
    public void DropItem()
    {
        foreach (Transform child in transform)
        {
            child.GetComponent<spawn>().SpawnDroppedItem();//essa linha aqui é depois do script spawn
            GameObject.Destroy(child.gameObject);
        }
    }
```
## 🏵️ Segundo passo ##

Crie um `C# Script` chamado `DropItems`.

# Bibliotecas #
```
/*bibliotecas aqui*/
```
# Variáveis iniciais #
```
    public GameObject item;
    private Transform player;
```

# Código

```
    void Start()
    {
        player = GameObject.FindGameObjectWithTag("Player").transform;
        
    }
```
#
```
    public void SpawnDroppedItem()
    {
        Vector2 playerPos = new Vector2(player.position.x, player.position.y + 3);
        Instantiate(item, playerPos, Quaternion.identity);
    }
```


# Dependências
#
<Tip>BoxCollision2D</Tip>
<Tip>Rigidbody2D</Tip>

`🏷️ Unity3D` `🟣Unity3D`
