---
title: 'Porta Abrindo com Pressão 2D | Unity'
---
# Bibliotecas #
``` 
//default libraries
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

```

# Variáveis iniciais #
```
    public GameObject door;
    public float heightMove = 5f;
    private bool isOpened;
````

# Código #

```
    private void OnTriggerEnter2D(Collider2D collision)
    {
        if (collision.gameObject.CompareTag("Player"))
        {
            if (!isOpened)
            {
                isOpened = true;
                door.transform.position += new Vector3(0, -heightMove, 0);
            }
        }        
    } 
```
#
<Warning>Esse script deve ser atrelado ao GameObject responsável pela pressão.</Warning>


# Dependências #

<Tip>BoxCollision2D as Trigger</Tip>
<Tip>Tag</Tip>


