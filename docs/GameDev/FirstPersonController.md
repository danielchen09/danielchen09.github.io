# First Person Controller
## Sources
- [https://www.youtube.com/watch?v=_QajrabyTJc](https://www.youtube.com/watch?v=_QajrabyTJc)
- [https://www.youtube.com/watch?v=7KiK0Aqtmzc](https://www.youtube.com/watch?v=7KiK0Aqtmzc)

## Set up
- Player {Character Controller, Movement Script}
    - Model
    - Main Camera {Look Script}
    - Ground Check
- Set ground layer and ground check of movement script

## Camera Script
```c#
public class LookController : MonoBehaviour {
    private float xRotation;
    public float sensitivity = 100f;

    private GameObject player;

    private void Start() {
        player = GameObject.Find("Player");
    }

    void Update() {
        float mouseX = Input.GetAxis("Mouse X") * sensitivity * Time.deltaTime;
        player.transform.Rotate(Vector3.up * mouseX);

        float mouseY = Input.GetAxis("Mouse Y") * sensitivity * Time.deltaTime;
        xRotation = Mathf.Clamp(xRotation - mouseY, -90f, 90f);

        transform.localRotation = Quaternion.Euler(xRotation, 0f, 0f);
    }
}
```

## Movement Script
```c#
public class MoveController : MonoBehaviour {
    private CharacterController controller;
    public Transform groundCheck;
    private Vector3 move;
    private Vector3 velocity;
    public bool isGrounded;

    public float speed = 6f;
    public float jumpSpeed = 5f;
    public float fallMultiplier = 2.5f;
    public float lowJumpMultiplier = 2f;
    public float gravity = -2f;
    public float groundDistance = .1f;
    public LayerMask groundMask;

    void Start() {
        controller = GetComponent<CharacterController>();

        Cursor.lockState = CursorLockMode.Locked;
    }

    void Update() {
        float x = Input.GetAxis("Horizontal");
        float z = Input.GetAxis("Vertical");

        move = transform.right * x + transform.forward * z;

        isGrounded = Physics.CheckSphere(groundCheck.position, groundDistance, groundMask);
        if (isGrounded && velocity.y < 0)
            velocity.y = -2f;

        if (Input.GetButtonDown("Jump") && isGrounded) {
            velocity.y = jumpSpeed;
        }

        velocity.y += gravity * Time.deltaTime;
        controller.Move(velocity * Time.deltaTime);
        
        controller.Move(move * speed * Time.deltaTime);
    }
}
```

## Better Jumping
- Add before applying gravity

```c#
if (velocity.y < 0) {
    // is falling
    velocity += Vector3.up * gravity * fallMultiplier * Time.deltaTime;
} else if (velocity.y > 0 && !Input.GetButton("Jump")) {
    // is still going up, but not holding jump button, fall faster
    velocity += Vector3.up * gravity * lowJumpMultiplier * Time.deltaTime;
}
// otherwise fall fall normally
```