```
PLAY [all] *************************************************************************************************************************************************************************************************

TASK [Gathering Facts] *************************************************************************************************************************************************************************************
ok: [vm]

TASK [docker : Load OS-specific vars.] *********************************************************************************************************************************************************************
ok: [vm]

TASK [docker : include_tasks] ******************************************************************************************************************************************************************************
skipping: [vm]

TASK [docker : include_tasks] ******************************************************************************************************************************************************************************
included: /home/emileyray/Документы/GitHub/devops-lab-4/ansible/roles/docker/tasks/setup-Debian.yml for vm

TASK [docker : Ensure old versions of Docker are not installed.] *******************************************************************************************************************************************
ok: [vm]

TASK [docker : Ensure dependencies are installed.] *********************************************************************************************************************************************************
ok: [vm]

TASK [docker : Ensure additional dependencies are installed (on Ubuntu < 20.04 and any other systems).] ****************************************************************************************************
skipping: [vm]

TASK [docker : Ensure additional dependencies are installed (on Ubuntu >= 20.04).] *************************************************************************************************************************
ok: [vm]

TASK [docker : Add Docker apt key.] ************************************************************************************************************************************************************************
ok: [vm]

TASK [docker : Ensure curl is present (on older systems without SNI).] *************************************************************************************************************************************
skipping: [vm]

TASK [docker : Add Docker apt key (alternative for older systems without SNI).] ****************************************************************************************************************************
skipping: [vm]

TASK [docker : Add Docker repository.] *********************************************************************************************************************************************************************
ok: [vm]

TASK [docker : Install Docker packages.] *******************************************************************************************************************************************************************
skipping: [vm]

TASK [docker : Install Docker packages (with downgrade option).] *******************************************************************************************************************************************
ok: [vm]

TASK [docker : Install docker-compose plugin.] *************************************************************************************************************************************************************
skipping: [vm]

TASK [docker : Install docker-compose-plugin (with downgrade option).] *************************************************************************************************************************************
skipping: [vm]

TASK [docker : Ensure /etc/docker/ directory exists.] ******************************************************************************************************************************************************
skipping: [vm]

TASK [docker : Configure Docker daemon options.] ***********************************************************************************************************************************************************
skipping: [vm]

TASK [docker : Ensure Docker is started and enabled at boot.] **********************************************************************************************************************************************
ok: [vm]

TASK [docker : Ensure handlers are notified now to avoid firewall conflicts.] ******************************************************************************************************************************

TASK [docker : include_tasks] ******************************************************************************************************************************************************************************
included: /home/emileyray/Документы/GitHub/devops-lab-4/ansible/roles/docker/tasks/install-compose.yml for vm

TASK [docker : Check current docker-compose version.] ******************************************************************************************************************************************************
ok: [vm]

TASK [docker : set_fact] ***********************************************************************************************************************************************************************************
ok: [vm]

TASK [docker : Delete existing docker-compose version if it's different.] **********************************************************************************************************************************
--- before
+++ after
@@ -1,4 +1,4 @@
 {
     "path": "/usr/local/bin/docker-compose",
-    "state": "file"
+    "state": "absent"
 }

changed: [vm]

TASK [docker : Install Docker Compose (if configured).] ****************************************************************************************************************************************************
changed: [vm]

TASK [docker : Get docker group info using getent.] ********************************************************************************************************************************************************
skipping: [vm]

TASK [docker : Check if there are any users to add to the docker group.] ***********************************************************************************************************************************

TASK [docker : include_tasks] ******************************************************************************************************************************************************************************
skipping: [vm]

TASK [docker : include_tasks] ******************************************************************************************************************************************************************************
included: /home/emileyray/Документы/GitHub/devops-lab-4/ansible/roles/docker/tasks/docker-pip-python.yml for vm

TASK [docker : Check python3-pip installation] *************************************************************************************************************************************************************
ok: [vm]

TASK [docker : Install docker libraries] *******************************************************************************************************************************************************************
ok: [vm]

TASK [web_app : Wipe base path] ****************************************************************************************************************************************************************************
skipping: [vm]

TASK [web_app : Create a directory if it doesn't exist] ****************************************************************************************************************************************************
--- before
+++ after
@@ -1,4 +1,4 @@
 {
     "path": "opt/web_app",
-    "state": "absent"
+    "state": "directory"
 }

changed: [vm]

TASK [web_app : Create docker compose] *********************************************************************************************************************************************************************
--- before
+++ after: /home/emileyray/Документы/GitHub/devops-lab-4/ansible/roles/docker/tasks/docker-compose.yml
@@ -0,0 +1,9 @@
+version: "3"
+
+services:
+    web_app:
+        image: 'emileyray/flask:latest'
+        ports: 
+            - "5050:5050"
+        restart: always
\ No newline at end of file
changed: [vm]
TASK [web_app : Start services] ****************************************************************************************************************************************************************************
changed: [vm]
PLAY RECAP *************************************************************************************************************************************************************************************************
vm                        : ok=20   changed=10   unreachable=0    failed=0    skipped=13   rescued=0    ignored=0   
```