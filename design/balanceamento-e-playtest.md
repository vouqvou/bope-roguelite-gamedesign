# BOPE Roguelite Mobile — Balanceamento & Playtest (v1)

> Game Designer deliverable. Baseado na pesquisa de waves de titulos wave-survival
> (Vampire Survivors e similares) e adaptado ao core do BOPE Roguelite Mobile.

## 1. Core Gameplay Loop
1. Entrar na sala -> spawn de waves (roguelite room clear)
2. Mover (drag touch) + tiro automatico no inimigo mais proximo
3. Sobreviver a densidade crescente + elite/mini-boss
4. Limpar sala -> loot / power-up -> escolher proxima sala (progressao roguelite)
5. Repetir com dificuldade escalada -> boss de andar -> extracao

## 2. Curva de Waves (janela por minuto)
| Janela | Densidade | HP inimigo | Dano | Papel de design |
|--------|-----------|------------|------|-----------------|
| 0-2min | baixa, trickle | ~5 HP | baixo | ensina movimento/kiting |
| 2-5min | fluxo constante | 10-20 HP | baixo-med | janela de upar armas |
| 5-10min | bursts alta densidade | 30-80 HP | medio | swarm event a cada ~1min |
| 10-15min | elite + adds | 300-1000 HP | alto | mini-boss por marcador |
| 30min | multi-spawn instantaneo | invuln/9999 | instakill | hard timer / fim da run |

## 3. Escalonamento de Dificuldade
- **HP scaling:** HP_base * (1 + 0.12 * sala) — +12% por sala.
- **Densidade:** spawn_rate * (1 + 0.08 * minuto).
- **Dano:** dmg_base * (1 + 0.06 * andar).
- **Elite cadence:** 1 elite a cada 2 salas; boss de andar a cada 5 salas.

## 4. Niveis de Dificuldade
| Nivel | Mult. HP | Mult. Dano | Mult. Densidade | Loot |
|-------|----------|-----------|-----------------|------|
| Recruta | 0.8 | 0.8 | 0.85 | +20% |
| Operador | 1.0 | 1.0 | 1.0 | 1.0 |
| Caveira | 1.3 | 1.2 | 1.25 | -10% |
| Comando | 1.6 | 1.4 | 1.5 | -20% |

## 5. Skills / Power-ups (arvore inicial)
- **Tiro rapido:** -15% cooldown de disparo (3 niveis).
- **Cadencia dupla:** +1 projetil por rajada.
- **Colete tatico:** +25 HP max.
- **Adrenalina:** +12% move speed ao levar dano (5s).
- **Municao perfurante:** projetil atravessa 1 inimigo.
- **Granada de fragmentacao:** AoE a cada 8s.

## 6. Inimigos (mapeados no core)
- **Vapor (basico):** rush, baixo HP, ensina mira automatica.
- **Faccao leve:** medio HP, dispara a distancia.
- **Blindado:** alto HP, lento, forca reposicionamento.
- **Elite/mini-boss:** padrao de spawn scriptado no marcador de minuto/sala.

## 7. Plano de Playtest
- Sessao A: validar curva 0-10min (retencao, mortes por janela).
- Sessao B: TTK (time-to-kill) por tipo de inimigo vs. build.
- Sessao C: leitura de dificuldade (Recruta vs Caveira) e taxa de clear de sala.
- Metricas alvo: TTK basico < 0.8s; morte media da run entre sala 6-9 no Operador.

## 8. Proximos ajustes propostos
- Reduzir HP do blindado em -10% se clear de sala > 90s no Operador.
- Adicionar janela de respiro (2s) apos elite antes do proximo burst.
- Balancear loot para garantir 1 power-up ofensivo por 2 salas.
