using UnityEngine;

public class NewEmptyCSharpScript : MonoBehaviour
{
    public float rotationSpeed = 60f;

    void Update()
    {
        float yaw = Input.GetAxis("Horizontal") * rotationSpeed * Time.deltaTime;
        float pitch = Input.GetAxis("Vertical") * rotationSpeed * Time.deltaTime;
        Quaternion yawRotation = Quaternion.AngleAxis(yaw, Vector3.up);
        Quaternion pitchRotation = Quaternion.AngleAxis(pitch, Vector3.right);
        transform.rotation = yawRotation * pitchRotation * transform.rotation;
    }
    
}
using UnityEngine;

public class CameraFollow : MonoBehaviour
{
    public Transform target;
    public Vector3 offset =  new Vector3(0, 5, -10);
    private void LateUpdate()
    {
        if (target != null)
        {
            transform.position = target.position + offset;
            transform.LookAt(target);
        }
    }
}


