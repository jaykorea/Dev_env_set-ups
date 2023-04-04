# install nginx
```
sudo apt-get install nginx
```
# configure nginx file on /etc/nginx/sites-available/rgbanalyzer
```                                                               
upstream django_app {
    server 127.0.0.1:8001;
}

server {
    listen 80;
    server_name www.zeroexposure1905.com;

    location / {
        proxy_pass http://django_app;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }

    location /static/ {
        alias /home/ubuntu/RGB_Analyzer_django_react/django_backend/src/staticfiles/;
    }

    location /media/ {
        alias /home/ubuntu/RGB_Analyzer_django_react/django_backend/media_root/;
    }
}

```
# link nginx file
```
sudo ln -s /etc/nginx/sites-available/rgbanalyzer /etc/nginx/sites-enabled/
```
# restart nginx
```
sudo systemctl restart nginx
```
# install gunicorn
```
pip install gunicorn
```
# launch server with gunicorn on root folder(for mine)
```
gunicorn --bind 0.0.0.0:8001 whatimage.wsgi:application
```
# request example
```
getImages = () => {
    axios.get(`https://www.zeroexposure1905.com/api/images/`, {
        headers: {
            'accept': 'application/json'
        }
    }).then(resp => {
        this.setState({
            images: resp.data,
            status: true
        })
        console.log(resp)
    })
    this.setState({ isLoading: false })
};
```
