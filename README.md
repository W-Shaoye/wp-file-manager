

![image](https://github.com/W-Shaoye/wp-file-manager/blob/main/image.png)


Although the code checks for an administrator login on line 54, the API route remains open to everyone on lines 58 and 64 because the permission_callback is set to __return_true.

Here's the issue: even after the administrator logs out, the API still exists.
It remains accessible, with no mechanism to prevent non-administrators from accessing it.
Once the REST API route is registered, WordPress does not revalidate current_user_can('manage_options').
As a result, any visitor, including unauthenticated users, can access this API.

