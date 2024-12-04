import java.io.IOException;
import java.net.HttpURLConnection;
import java.net.URL;

public class URLRedirect {
    public static void main(String[] args) {
        // URL original
        String urlOriginal = "https://iplayerhls.com/e/9mnvawcbyx4k";
        
        try {
            // Crear un objeto URL con la URL original
            URL url = new URL(urlOriginal);
            // Abrir una conexión HTTP
            HttpURLConnection connection = (HttpURLConnection) url.openConnection();
            
            // Establecer método de solicitud a GET
            connection.setRequestMethod("GET");
            connection.setInstanceFollowRedirects(false); // Evitar redirección automática
            
            // Conectar
            connection.connect();
            
            // Obtener el código de respuesta HTTP
            int statusCode = connection.getResponseCode();
            
            if (statusCode == HttpURLConnection.HTTP_OK) {
                // Si la conexión es exitosa, obtener la URL final
                String finalURL = connection.getURL().toString();
                
                // Verificar si la URL termina en .m3u8
                if (finalURL.endsWith(".m3u8")) {
                    System.out.println("La URL final es: " + finalURL);
                } else {
                    System.out.println("La URL no termina en .m3u8, la URL final es: " + finalURL);
                }
            } else if (statusCode == HttpURLConnection.HTTP_MOVED_TEMP || statusCode == HttpURLConnection.HTTP_MOVED_PERM) {
                // Si hay redirección (301 o 302), obtener la URL de redirección
                String redirectURL = connection.getHeaderField("Location");
                System.out.println("La URL redirigida es: " + redirectURL);
            } else {
                System.out.println("Error: Código de estado HTTP " + statusCode);
            }
            
        } catch (IOException e) {
            System.out.println("Error al realizar la solicitud: " + e.getMessage());
        }
    }
}
