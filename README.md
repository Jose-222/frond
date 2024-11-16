# frond
Instrucciones para Frontend (Next.js)
Requisitos previos
Tener Node.js instalado (preferiblemente la versión LTS).
Tener npm o yarn instalado.
1. Clonar el Repositorio del Frontend
Si aún no has clonado el proyecto:

bash
Copiar código
git clone <URL_DEL_REPOSITORIO_FRONTEND>
cd tipo-cambio-frontend
2. Instalación de Dependencias
Primero, instala las dependencias del proyecto utilizando npm:

bash
Copiar código
npm install
Este comando instalará todas las dependencias necesarias, como axios, tailwindcss y recharts.

3. Configuración de Tailwind CSS
Asegúrate de que el archivo tailwind.config.js esté configurado correctamente. Si no tienes este archivo, crea uno con el siguiente contenido:
javascript
Copiar código
module.exports = {
  content: [
    './pages/**/*.{js,ts,jsx,tsx}',
    './components/**/*.{js,ts,jsx,tsx}',
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
Asegúrate de que en el archivo src/styles/globals.css tengas las directivas para Tailwind:
css
Copiar código
@tailwind base;
@tailwind components;
@tailwind utilities;
4. Configuración de la URL del Backend
En el archivo src/pages/index.js, configura la URL de tu backend. Asegúrate de que el backend esté ejecutándose en http://localhost:8080 (o la URL correspondiente).

javascript
Copiar código
const fetchTipoCambio = async () => {
  try {
    const response = await axios.get('http://localhost:8080/api/tipo-cambio/ultimo');
    setTipoCambio(response.data);
  } catch (error) {
    console.error('Error al obtener el tipo de cambio:', error);
  } finally {
    setLoading(false);
  }
};
5. Ejecutar el Frontend
Para ejecutar el frontend, usa el siguiente comando:

bash
Copiar código
npm run dev
Esto iniciará el servidor de desarrollo de Next.js en http://localhost:3000. La página mostrará el tipo de cambio y se actualizará automáticamente cada 30 segundos.
