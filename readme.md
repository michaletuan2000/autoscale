
# apply all 
    ka -f 1.deployment.yaml
    ka -f 2.hpa.yaml


# delete all
    kd -f 1.deployment.yaml
    kd -f 2.hpa.yaml

# test loading via service
    k run -i --tty load-generator --rm --image=busybox:1.28 --restart=Never -- /bin/sh -c "while sleep 0.01; do wget -q -O- http://php-apache; done"

# delete test loading 
     kd pod load-generator

# watch hpa
    kg hpa php-apache-hpa --watch

# run argocd-application
    ka -f 0.argo-application.yaml