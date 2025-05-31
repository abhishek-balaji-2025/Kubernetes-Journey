Deployment commands

19. Update the Image Used by a Deployment

kubectl set image deployment/<deployment-name> <container-name>=<image-name>:<tag>

Example:
kubectl set image deployment/test2 nginx=nginx:latest

Functionality:
This command updates the container image used by a deployment. In this example, it sets the image for the container named nginx in the deployment test2 to nginx:latest.

✅ Note:

The container name (nginx in this case) must match the container defined in the deployment spec.

This command triggers a rolling update by default.

20. Check the Rollout Status of a Deployment

`kubectl rollout status deployment/<deployment-name>`

Example:
`kubectl rollout status deployment/mydeployment`

Functionality:
This command shows the status of the rollout for the specified deployment. It helps you monitor whether a new deployment or image update has completed successfully or is still in progress.

✅ Tip: Use this after changing the image or updating deployment configurations to ensure the update rolled out properly.

21. To undo a rollout use the command

`kubectl rollout undo deployment <deployment-name>`

Example:
`kubectl rollout undo deployment test2`

Functionality:
Reverts the deployment to the previous version in case the current rollout caused issues. Useful for quick rollback if something goes wrong after updating the deployment.

22. To check rollout history

`kubectl rollout history deployment <deployment-name>`

Example:

`kubectl rollout history deployment test2`

Functionality:
Displays the revision history of a Kubernetes deployment. This allows you to view previous versions of the deployment and track changes over time.
