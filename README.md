# Ex3---Hurdle-Game-2D

## AIM:
To develop a 2D game using C# program in unity .

## ALGORITHM:
### STEP 1:
Create a 2D project in unity.

### STEP 2:
Add player,hurdles,coins,track in the frame and add the valid 2D collider component.

### STEP 3:
Click Assets->Create->C# Script.

### STEP 4:
Create player.cs and score.cs and add c# code.

### STEP 5:
Click canvas->Gamemanager->add Score and value.

### STEP 6:
Drag the script to player and coin.

### STEP 7:
Run the scene and display the output.

## PROGRAM:
Developed by:SETHUKKARASI C<br>
Register Number:212223230201
### player.cs:
```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class player : MonoBehaviour
{
    public float speed;
    public float jumpforce;
    private Rigidbody2D rb;
    public Score cc;
    // Start is called before the first frame update
    void Start()
    {
        rb = GetComponent<Rigidbody2D>();
    }

    // Update is called once per frame
    void Update()
    {
        float moveinp = Input.GetAxisRaw("Horizontal");
        transform.position += new Vector3(moveinp, 0, 0) * speed * Time.deltaTime;
        if (Input.GetKeyDown(KeyCode.Space) && Mathf.Abs(rb.velocity.y) < 0.001f)
        {
            rb.AddForce(new Vector2(0, jumpforce), ForceMode2D.Impulse);
        }
    }
    private void OnTriggerEnter2D(Collider2D other)
    {
        if(other.CompareTag("Destroy"))
        {
            cc.coincount++;
            Destroy(other.gameObject);
        }
    }
}
```

### Score.cs:
```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;

public class Score : MonoBehaviour
{
    public int coincount;
    public Text value;
    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        value.text = coincount.ToString();
    }
}
```

## OUTPUT:
![output](/2dgame.png)
## RESULT:
Thus a 2D game using C# program in unity is developed successfully.