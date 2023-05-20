import requests

def get_posts() -> list : 
    response = requests.get(f"{URL}persons?$filter=isActive eq true and accessProfile eq 'Clientes'&token={TOKEN}")
    try:
        jsonrespose = response.json()
    except Exception as err:
       # err.args
        print(err.args)
        print(err.__class__) #erro que retorna a classe 
        print(err.__traceback__.tb_lineno) #linha do erro
        print(err)
        return list()
        
    else:
        return jsonrespose
    

def main():
    arrayRetornados:list = get_posts()
    arrayFiltrados:list
    arrayDesconsiderados:list
   
    for post in arrayRetornados: 
        post: dict

        # ID de relacionamento igual a 1 
        if any(relationship['id'] == '1' for relationship in post['relationships']):
            arrayDesconsiderados.append(post.copy())
            continue 

        # Comparação == Agente
        if post['classification'].upper().trim() == "AGENTE":
            arrayDesconsiderados.append(post.copy())
            continue

        # tratamento ticket 3 meses
        else:
            arrayFiltrados.append(post.copy())


    print(arrayDesconsiderados)
    print(arrayFiltrados)

if "__main__" == __name__:
    main()

