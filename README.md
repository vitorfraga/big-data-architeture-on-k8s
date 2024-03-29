source "$(brew --prefix)/opt/kube-ps1/share/kube-ps1.sh"
PS1='$(kube_ps1)'$PS1


Links úteis.

- [K8S](https://kubernetes.io/)
- [12Factor](https://12factor.net/pt_br/)
- [Descomplicando o K8S](https://livro.descomplicandokubernetes.com.br/pt/day_two/descomplicando_kubernetes.html)
- Chaos Kube
- História K8S
- Botkube
- Certificação

Pré requisitos.

1. Instalar o Minikube para trabalhar de forma local.
2. Instalar kubectl
3. Instalar plugin de atalhos no .bash ou .zsh
4. Instalar o brew
5. instalar o Kubens e kubectx (Necessário instalar o homebrew antes)
6. instalar o helm
	1. Adicione no path
		1. echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"' >> /home/catho/.zprofile
		2. eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"
7. Criar conta em uma cloud, para criarmos nosso cluster k8s em outro contexto, que não seja o local. 
	1. Digital Ocean
	2. Configurar o contexto cloud no kubectl, para alterar entre contextos utilize o kubectx, dentro do contexto escolhido, você pode anterar entre namespaces utilizando o kubens
8. Criar repositório no github, o conteúdo deste repositório será aplicado no cluster de k8s através do ArgoCD.



Run Cluster on EKS

1. Configure aws credential and profile in ~/.aws
2. Get profile name and set in main.tf
3. cd iac/
4. terraform init
5. terraform plan
6. terraform apply
7. Configure kubectl to manage cluster 
   1. aws eks --region $(terraform output -raw region) update-kubeconfig \
    --name $(terraform output -raw cluster_name) --profile guru
8. kubectl --cluster-info
