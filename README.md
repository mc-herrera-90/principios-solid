# Principios SOLID

Los principios **SOLID** son cinco buenas prácticas de diseño orientado a objetos que ayudan a crear software más mantenible, extensible y flexible. Fueron popularizados por **Robert C. Martin (Uncle Bob)**.

---

## 🟡 S - Single Responsibility Principle (SRP)

> "Una clase debe tener una, y solo una, razón para cambiar."

Cada clase o módulo debe encargarse de una única funcionalidad del sistema. Separar responsabilidades evita que un cambio en una parte afecte innecesariamente a otras.

**Ejemplo:**

```java
// ❌ Mala práctica
class ReportManager {
    void generateReport() {...}
    void saveToPDF() {...}
    void sendByEmail() {...}
}

// ✅ Mejor práctica
class ReportGenerator {...}
class PDFExporter {...}
class EmailSender {...}











## 🌐 I - Principio de Segregación de Interfaces (ISP)

> "Los clientes no deben verse obligados a depender de interfaces que no utilizan"

### ❌ Ejemplo que viola el ISP
```java
interface DispositivoOficina {
    void imprimir();
    void escanear();
    void faxear();
}

class ImpresoraBasica implements DispositivoOficina {
    // Obligada a implementar métodos que no usa
    public void imprimir() { ... }
    public void escanear() { 
        throw new UnsupportedOperationException(); 
    }
    public void faxear() { 
        throw new UnsupportedOperationException(); 
    }
}


