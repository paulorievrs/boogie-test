---
title: 'Movimentação Plataforma 2D Unity'
---

# Variáveis iniciais

```
    public float MovementSpeed = 1.5f;
    private Rigidbody2D rb2d;
```
# Código
```
void Start()
    {
        rb2d = GetComponent<Rigidbody2D>();
    }
```
#
```
void Update()
    {
        var movement = Input.GetAxis("Horizontal");
        transform.position += new Vector3(movement, 0, 0) * Time.deltaTime * MovementSpeed;

        if (movement < 0)
        {
            transform.localScale = new Vector3(-1, 1, 1);
        }
        else
        {
            transform.localScale = new Vector3(1, 1, 1);
        }

    }

```

# Dependências
#
<Tip>BoxCollision2D</Tip>
<Tip>Rigidbody2D</Tip>

`🏷️ Unity3D` `🟣Unity3D`