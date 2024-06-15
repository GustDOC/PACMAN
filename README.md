# PACMAN
# Descrição do Jogo
Pacman é um jogo clássico de arcade onde o jogador controla o personagem Pacman através de um labirinto. 

# Instruções para Jogabilidade
# Controles
Teclas de Direção: Use as teclas de direção (cima, baixo, esquerda, direita) para mover o Pacman pelo labirinto.
# Objetivos
Evitar Fantasmas: Evite ser tocado pelos fantasmas. Se um fantasma tocar Pacman, o jogo  acaba.

# Regras
Fim de Jogo: O jogo termina quando o PacMan é pego pelos fantasmas.

![MenuPacMan](https://github.com/GustDOC/PACMAN/assets/89112032/9eafc928-10be-442f-b1fc-045f3a5c6c8e)

![Pacman1](https://github.com/GustDOC/PACMAN/assets/89112032/cf945365-6ab2-43f5-ba43-743bd823d2d1)

![Pacman2](https://github.com/GustDOC/PACMAN/assets/89112032/fe8dbae2-20a5-4eb5-8002-c40f63ec86ad)

# Script

Realizado a criação do script abaixo para controlar o comportamento de um fantasma (Ghost) no jogo. O script controla a movimentação do fantasma em direção ao jogador (target = "Player") e define o que acontece quando o fantasma colide com o jogador que seria o retorno para o Menu. Conforme o video acima é possivel visualizar a movimentação do mesmo e o retorno ao menu.

using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.SceneManagement; 

public class Ghost : MonoBehaviour
{
    public GameObject target;
    UnityEngine.AI.NavMeshAgent agent;

    // Start is called before the first frame update
    void Start()
    {
        agent =  GetComponent<UnityEngine.AI.NavMeshAgent>();
        if(target==null){
            target = GameObject.FindGameObjectWithTag("Player");
        }
    }

    // Update is called once per frame
    void Update()
    {
        agent.destination = target.transform.position;
    }

    public void OnCollisionEnter(Collision collision)
    {
        if (collision.gameObject.tag == "Player")
            SceneManager.LoadScene("Menu");
    }
}
