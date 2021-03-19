---
title: 'Pulo 2D Unity'
---


# Variáveis iniciais #
```
public float JumpForce = 5f;
````

# Código

```
if (Input.GetButtonDown("Jump") && Mathf.Abs(rb2d.velocity.y) < 0.001f)

    {
        anim.SetTrigger("isJump");
        rb2d.AddForce(new Vector2(0, JumpForce), ForceMode2D.Impulse);
    }        
```
# Dependências
#
<Tip>BoxCollision2D</Tip>
<Tip>Rigidbody2D</Tip>


