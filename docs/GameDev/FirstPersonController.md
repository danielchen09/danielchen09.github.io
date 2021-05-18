# First Person Controller
## Sources
- (https://www.youtube.com/watch?v=_QajrabyTJc)[https://www.youtube.com/watch?v=_QajrabyTJc]

## Set up
- Player {Character Controller, Movement Script}
    - Model
    - Main Camera {Look Script}
    - Ground Check

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
public class MoveController : MonoBehaviour
{
    private CharacterController controller;
    public Transform groundCheck;
    private Vector3 move;
    private Vector3 velocity;
    private bool isGrounded;

    public float speed = 6f;
    public float gravity = 2f;
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
            // handle jumping
        }

        velocity.y += gravity * Time.deltaTime;
        controller.Move(velocity * Time.deltaTime);
        
        controller.Move(move * speed * Time.deltaTime);
    }
}
```