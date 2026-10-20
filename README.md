# balanca-da-decisao

<!-- psicothica-kit 1.0.1 -->
**psicothica-kit 1.0.1**

Projeto: App de Tomada de Decisão Assertiva
Perfil Terapêutico: Terapia Cognitivo Comportamental de Terceira Onda
Público-alvo: Indivíduos com desregulação emocional, paralisia por análise, TDAH ou sobrecarga cognitiva durante momentos de tomada de decisão

Material informativo e de apoio da marca **Psicothica** (Alanne Raquel Fragoso de Farias, psicóloga, CRP 13/9646), disponível no Programa Ramificar da AyA Clínica Integrada. Não substitui avaliação, diagnóstico ou acompanhamento profissional.

Publicado no GitHub Pages: `https://psicothica.github.io/balanca-da-decisao/`.

## Como é feito

- Um único `index.html` (sem etapa de build) + a pasta `psi-kit/`, que é uma **cópia** do [psicothica-kit](https://github.com/psicothica/psicothica-kit) 1.0.1: `tokens.css`, `psi-components.css`, `fonts/` (WOFF2 locais, licenças OFL em `fonts/licenses/`), `logo/` e `js/psi-storage.js`. Não há submodule nem dependência entre repositórios.
- Nenhuma requisição externa: sem Google Fonts, sem CDN, sem analytics, sem IA. A única referência externa é o link de texto para o Instagram (`target="_blank" rel="noopener noreferrer"`) e os links `tel:` do rodapé.
- O cabeçalho e o rodapé são os do kit (o texto do rodapé não deve ser editado aqui). Dentro de um iframe (como no AyAClin) o cabeçalho fica compacto; aberto direto, fica completo.
- Para atualizar o kit: substitua o conteúdo de `psi-kit/` pelo da nova versão e atualize a linha `psicothica-kit x.y.z` no topo do `index.html` e deste README.

## Dados e privacidade

Tudo fica no `localStorage` do navegador, com o prefixo **`psi.balanca-da-decisao.v1.`**:

| Chave (sem o prefixo) | Conteúdo |
|---|---|
| `decisoes:lista` | Lista de decisões (título, opções, prós e contras com peso, intuição, reflexão) |
| `decisoes:atual` | Id da decisão em foco |

Todos os apps do Psicothica dividem a origem `psicothica.github.io`; por isso este app só lê, grava, exporta e apaga as chaves do próprio prefixo.

- **Exportar** (Histórico → "Exportar backup"): arquivo JSON do kit com metadados (`app`, `version`, `exportedAt`) e **só as chaves deste app**.
- **Importar**: aceita o arquivo novo e o formato antigo da Balança (`{ "app": "Ecossistema Psicothica", "dados": { "decisoes:lista": ... } }`), que é convertido na hora; só as chaves `decisoes:*` do arquivo antigo são aproveitadas. Arquivo de **outro app** é recusado, sem gravar nada.
- **Migração única** das chaves antigas (`psicothica:decisoes:lista` e `psicothica:decisoes:atual`): copia para o prefixo novo, confere a cópia e só então remove as chaves antigas desta app. Nenhuma outra chave (de outros apps) é lida, movida ou apagada.
- Se o navegador bloquear o armazenamento, o app avisa ("Seus registros não serão salvos neste navegador.") e funciona em memória.

## Testes locais

```bash
python -m http.server 8000     # e abra http://localhost:8000/
```

## Direitos autorais

Copyright (c) 2026 Alanne Raquel Fragoso de Farias. Todos os direitos reservados. Nenhuma parte deste software ou do seu conteúdo pode ser copiada, modificada, distribuída ou usada para fins comerciais sem autorização prévia e por escrito da autora.
