---
title: 'Cassino - LootBox 2D Unity'
---

# Bibliotecas #
```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;
using TMPro; 
```
nesse exemplo usamos uma técnica de inserir dois _scripts_ em um. 
Adicione o próximo _snippet_ acima da `public class MonoBehaviour` que vem por padrão ao criar um novo _script_.
```
[System.Serializable]
public class ItemToSpawn
{
    public GameObject item;
    public float spawnRate;
    public string itemName;

    [HideInInspector]
    public float minSpawnProb, maxSpawnProb;
}
```

# Variáveis iniciais #
```
    public Button reedemButton;
    public ItemToSpawn[] itemToSpawn;
    public TextMeshProUGUI textName;
    private GameObject current;
````

# Código

```
 void Start()
    {
        Button btn = reedemButton.GetComponent<Button>();

        /*responsible for the probability*/
        for(int i = 0; i < itemToSpawn.Length; i++)
        {
            if (i == 0)
            {
                itemToSpawn[i].minSpawnProb = 0;
                itemToSpawn[i].maxSpawnProb = itemToSpawn[i].spawnRate - 1 ;
            }
            else
            {
                itemToSpawn[i].minSpawnProb = itemToSpawn[i - 1].maxSpawnProb + 1;
                itemToSpawn[i].maxSpawnProb = itemToSpawn[i].minSpawnProb + itemToSpawn[i].spawnRate + 1;
            }

        }
    }       
```
#
```
public void Spawner()
    {
        if(current != null)
        {
            Destroy(current);
            current = null;
        }

        float randomNum = Random.Range(0, 100);
        Debug.Log(randomNum);

        for(int i=0; i < itemToSpawn.Length; i++)
        {
            if(randomNum >= itemToSpawn[i].minSpawnProb && randomNum <= itemToSpawn[i].maxSpawnProb
                && current == null)
            {
                GameObject obj = Instantiate(itemToSpawn[i].item, transform.position, Quaternion.identity);
                obj.name = itemToSpawn[i].itemName;
                textName.text = itemToSpawn[i].itemName;
                current = obj;
                break;
            }

        }

    }
```
#
```
public void OnClick()
    {
        Spawner();
    }
```
volte na void _Start()_ e adicione a função de clique:
```
    btn.onClick.AddListener(OnClick);
```
# Dependências #
<Tip>Itens Prefabs</Tip>
<Tip>Canvas Text & Button</Tip>


