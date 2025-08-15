# 🐱 Dashboard Interativo com The Cat API e Looker Studio

## 📌 Descrição do Projeto
Este projeto consiste em um **dashboard interativo** desenvolvido no **Looker Studio**, utilizando como fonte de dados a **The Cat API**.
O objetivo é apresentar informações sobre diferentes raças de gatos, incluindo **origem**, **expectativa de vida**, **temperamento** e **imagens**, de forma clara e visual.

---

## ✅ Objetivos
- Praticar integração de APIs com **Google Sheets**.
- Criar um dashboard interativo no **Looker Studio**.
- Demonstrar boas práticas em **Data Visualization**.

---

## 🔗 Ferramentas Utilizadas
- **The Cat API** – Fonte dos dados.
- **Google Sheets** – Intermediário para conexão com o Looker Studio.
- **Looker Studio** – Criação do dashboard.

---

## 🛠 Passo a Passo

### **1️⃣ Criar a API Key**
- Acesse [The Cat API](https://thecatapi.com/).
- Crie uma conta gratuita e gere sua **API Key**.

---

### **2️⃣ Obter os dados da API**
Você pode usar **Google Apps Script** para puxar os dados diretamente para o **Google Sheets**:

```javascript
function getCatBreeds() {
  var url = 'https://api.thecatapi.com/v1/breeds';
  var options = {
    'method': 'get',
    'headers': {
      'x-api-key': 'SUA_API_KEY_AQUI'
    }
  };

  var response = UrlFetchApp.fetch(url, options);
  var data = JSON.parse(response.getContentText());

  var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  sheet.clear();
  
  sheet.appendRow(["Name", "Origin", "Temperament", "Life Span", "Image_URL"]);
  
  data.forEach(function(breed) {
    sheet.appendRow([
      breed.name,
      breed.origin,
      breed.temperament,
      breed.life_span,
      breed.image ? breed.image.url : ""
    ]);
  });
}
```

✅ **Salve e execute no Apps Script** (dentro do Google Sheets) para carregar os dados.

---

### **3️⃣ Conectar o Google Sheets ao Looker Studio**
- Abra o **Looker Studio**.
- Clique em **Criar → Fonte de dados → Google Sheets**.
- Selecione a planilha com os dados carregados pela API.
- Conecte e configure os campos (por exemplo, `Image_URL` como tipo **Imagem**).

---

### **4️⃣ Criar o Dashboard**
Inclua os seguintes elementos:
✔️ **Gráfico de pizza**: distribuição de raças por origem.
✔️ **Mapa interativo**: localizações das raças.
✔️ **Tabela com imagens**: foto, temperamento e expectativa de vida.
✔️ **Filtros dinâmicos**: por origem e temperamento.

---

### **5️⃣ Publicar**
- Publique o dashboard no modo **visualização pública**.
- Inclua o link aqui no repositório.

---

## 📸 Preview do Dashboard
<img width="421" height="632" alt="image" src="https://github.com/user-attachments/assets/1a8efaa9-4cac-4335-8950-ce2aada7ec65" />

---

## 📎 Link para o Dashboard
[[Acesse o Dashboard no Looker Studio](INSIRA_AQUI_SEU_LINK)](https://lookerstudio.google.com/reporting/23374a29-55b7-4bf0-8c9a-b97dee63c266/page/K8RUF?s=voEct50Pb4g)

---

## 📚 Aprendizados
✔️ Integração de APIs em dashboards.

✔️ Boas práticas em **Data Visualization**.

✔️ Uso do **Looker Studio** para dashboards interativos.
