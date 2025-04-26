# 🚀 Build Custom Docker Image for ERPNext Healthcare

## 🛠️ Build Custom Image
### Windows
<pre>$encoded = [Convert]::ToBase64String([System.Text.Encoding]::UTF8.GetBytes((Get-Content "development\apps.json" -Raw))); 
docker build -t erpnext-healthcare-custom --build-arg FRAPPE_PATH=https://github.com/frappe/frappe --build-arg FRAPPE_BRANCH=version-15 --build-arg PYTHON_VERSION=3.11.6 --build-arg NODE_VERSION=18.18.2 --build-arg APPS_JSON_BASE64=$encoded -f images/custom/Containerfile .
</pre>
### Linux
<pre>encoded=$(base64 -w 0 development/vscode-example/apps.json)
docker build -t erpnext-healthcare-custom   --build-arg FRAPPE_PATH=https://github.com/frappe/frappe   --build-arg FRAPPE_BRANCH=version-15   --build-arg PYTHON_VERSION=3.11.6   --build-arg NODE_VERSION=18.18.2   --build-arg APPS_JSON_BASE64="$encoded"   -f images/custom/Containerfile .
</pre>


## ⚙️ Easy Install Script
<pre>python easy-install.py deploy --project=erpnext_healthcare_prod --image=erpnext-healthcare-custom --version=latest --sitename=healthcare.local --email=ahmadgt710@gmail.com --http-port=9003 --no-ssl --app=erpnext --app=healthcare
</pre>
