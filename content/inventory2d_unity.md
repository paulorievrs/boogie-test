---
title: 'Sistema de Inventário 2D - Parte 1'
---

_ ⭐ Se você é iniciante recomendamos configurar primeiramente a movimentação do seu personagem antes de iniciar esse tutorial._

## 🏵️ Primeiro passo ##
Crie um `C# Script` chamado `Inventory`.

# Bibliotecas #
```
/*default librarys*/
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
```

# Variáveis iniciais #
```
    public bool[] isFull;
    public GameObject[] slots;
```
#
<Warning>Esse script deve ser atrelado ao GameObject responsável pela coleta de items. Exemplo: player.
</Warning>



## 🏵️ Segundo passo ##

Crie um `C# Script` chamado `PickUp`.

# Bibliotecas #
```
/*default librarys*/
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
```

# Variáveis iniciais #
```
    private Inventory inventory; //warning tip*
    public GameObject itemButton;
```


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
    private void OnTriggerEnter2D(Collider2D collision)
    {
        if(collision.gameObject.CompareTag("Player"))
        {
            for (int i = 0; i < inventory.slots.Length; i++)
            {
                if(inventory.isFull[i] == false)
                {
                    //ITEM CAN BE ADDED TO INVENTORY!
                    inventory.isFull[i]= true;
                    Instantiate(itemButton, inventory.slots[i].transform, false);
                    Destroy(gameObject);
                    break;
                }
            }
        }
    }
```

<Warning>Esse script deve ser atrelado ao GameObject coletável. Exemplo: poção de vida, espada, bloco de pedra.
</Warning>

#

## 🏵️ Terceiro passo ##
Crie um componente `Canvas` na tela `Hierarchy`.

# Dependências
#
<Tip>BoxCollision2D</Tip>
<Tip>Rigidbody2D</Tip>

`🏷️ Unity3D` `🟣Unity3D`
