# qt-test-application


mysql.svc.cluster.local
user.qtapp.svc.cluster.local
payment.svc.cluster.local
order.svc.cluster.local


rm -rf ./helm/user/user.yaml
helm template ./helm/user/ > ./helm/user/user.yaml

rm -rf ./helm/payment/payment.yaml
helm template ./helm/payment/ > ./helm/payment/payment.yaml


rm -rf ./helm/order/order.yaml
helm template ./helm/order/ > ./helm/order/order.yaml


kubectl apply -f /home/nagarjuna/go/src/github.com/naga2HPE/qt-test-application/helm/user/user.yaml -n qtapp
kubectl apply -f /home/nagarjuna/go/src/github.com/naga2HPE/qt-test-application/helm/payment/payment.yaml -n qtapp
kubectl apply -f /home/nagarjuna/go/src/github.com/naga2HPE/qt-test-application/helm/order/order.yaml -n qtapp

kubectl delete -f /home/nagarjuna/go/src/github.com/naga2HPE/qt-test-application/helm/user/user.yaml -n qtapp
kubectl delete -f /home/nagarjuna/go/src/github.com/naga2HPE/qt-test-application/helm/payment/payment.yaml -n qtapp
kubectl delete -f /home/nagarjuna/go/src/github.com/naga2HPE/qt-test-application/helm/order/order.yaml -n qtapp


https://kubernetes.io/docs/tasks/run-application/run-single-instance-stateful-application/
kubectl apply -f https://k8s.io/examples/application/mysql/mysql-pv.yaml -n mysql
kubectl apply -f https://k8s.io/examples/application/mysql/mysql-deployment.yaml -n mysql


kubectl delete -f https://k8s.io/examples/application/mysql/mysql-pv.yaml -n mysql
kubectl delete -f https://k8s.io/examples/application/mysql/mysql-deployment.yaml -n mysql



kubectl port-forward service/user 8080:8090 -n qtapp