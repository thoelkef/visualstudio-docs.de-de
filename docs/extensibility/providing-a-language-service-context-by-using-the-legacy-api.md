---
title: "Bietet einen Dienstkontext Sprache mit der Legacy-API | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] legacy - Language-Dienstkontext"
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Bietet einen Dienstkontext Sprache mit der Legacy-API
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Es gibt zwei Möglichkeiten, damit ein Sprachdienst Benutzerkontext mit dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Kern editors bereitstellt: Bereitstellen Textmarkierungs Elementkontext oder stellen Sie den Benutzerkontext bereit.  Die Unterschiede zwischen beiden werden hier erläutert.  
  
 Weitere Informationen über das Bereitstellen des Kontexts in ein Sprachdienst, der verbunden ist, Editors sind, finden Sie unter [Gewusst wie: Bereitstellen von Kontext für Editoren](../extensibility/how-to-provide-context-for-editors.md).  
  
## Stellen Sie Textmarkierungs\-Kontext in den Editor bereit  
 Um Kontext für die Compilerfehler bereitzustellen, die von Textmarkierungen im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Kern des Editors angegeben werden, implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>\-Schnittstelle.  In diesem Szenario stellt der Sprachdienst Kontext bereit, wenn der Cursor in einer Textmarkierung ist.  Dadurch kann der Editor verwendet, um das Schlüsselwort am Cursor an den **Dynamische Hilfe** Fenster ohne Attribute bereitzustellen.  
  
## Stellen Sie alle Benutzer\-Kontext in den Editor bereit  
 Wenn Sie einen Sprachdienst und verwenden den [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Kern des Editors erstellen, können Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>\-Schnittstelle implementieren, um Kontextinformationen für den Sprachdienst bereitzustellen.  
  
 Für die Implementierung von `IVsLanguageContextProvider`, wird ein Kontext behälter \(Auflistung\) für den Editor angefügt, der zum Aktualisieren des Kontexts behälters zuständig ist.  Wenn das Fenster **Dynamische Hilfe** die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A>\-Schnittstelle in diesem Kontext behälter an der Leerlaufzeit behälter Kontext aufruft, die fragt den Editor für ein Update.  Der Editor benachrichtigt den Sprachdienst, dass er den Editor aktualisieren soll, und übergibt einen Zeiger auf den Kontext behälter.  Hierzu wird die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A>\-Methode vom Editor zum Sprachdienst aufruft.  Verwenden des Zeigers auf den Kontext behälter, kann der Sprachdienst Attribute und Schlüsselwörter jetzt hinzufügen und entfernen.  Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>.  
  
 Es gibt zwei Möglichkeiten, `IVsLanguageContextProvider`zu implementieren:  
  
-   Erstellen Sie ein Schlüsselwort bereit behälter Kontext  
  
     Wenn der Editor aufgerufen wird, um den Kontext behälter zu aktualisieren, geben übergeben Sie den geeigneten Schlüsselwörtern und Attribute und dann `S_OK`zurück.  Dieser Rückgabewert weist den Editor an, um den Kontext beizubehalten Attribut aus Schlüsselwörtern und bereitstellen, anstatt das Schlüsselwort am Cursor auf den Kontext behälter.  
  
-   Abrufen des Schlüsselworts vom Schlüsselwort am Cursor  
  
     Wenn der Editor aufgerufen wird, um den Kontext behälter zu aktualisieren, übergeben Sie die entsprechenden Attribute und geben Sie dann in `E_FAIL`.  Dieser Rückgabewert weist den Editor auf, um die Attribute im Kontext behälter beizubehalten, sondern aktualisiert den Kontext behälter mit dem Schlüsselwort am Cursor.  
  
 Das folgende Diagramm zeigt, wie der Kontext für einen Sprachdienst bereitgestellt wird, der `IVsLanguageContextProvider`implementiert.  
  
 ![LangServiceImplementation2&#45;Grafik](~/docs/extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
Kontext für einen Sprachdienst  
  
 Wie Sie im Diagramm finden können, hat der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Kern text\-editor einen Kontext, der behälter daran angefügt wird.  Punkte dieses Kontexts behälters zu drei verschiedenen Unterkontext behältern: Sprachdienst, Standard\-Editor und Textmarkierung.  Die Sprachendienst\- und Textmarkierungs unterkontext behälter enthalten Attribute und Schlüsselwörter für den Sprachdienst, wenn die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>\-Schnittstelle implementiert wird, und die Textmarkierungen, wenn die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>\-Schnittstelle implementiert wird.  Wenn Sie einem dieser Schnittstellen implementieren, stellt der Editor Kontext für das Schlüsselwort an der Cursorposition im Unterkontext behälter des standardmäßigen Editor bereit.  
  
## Kontext\-Richtlinien für Editoren und Designer  
 Designer und Editoren müssen ein allgemeines Schlüsselwort für das Editor\- oder Designerfenster bereitstellen.  Dies erfolgt, damit ein generisches, aber ein entsprechendes, Hilfethema für den Designer oder den Editor anzeigen, wenn ein Benutzer F1 drückt.  Ein Editor muss, zusätzlich zu diesem, der das aktuelle Schlüsselwort am Cursor anzugeben oder einen Schlüsselbegriff auf Grundlage der aktuellen Auswahl bereitgestellt werden.  Dies geschieht, um sicherzustellen, dass ein Hilfethema für den Text oder UI\-Element auf sich selbst zeigten oder das Anzeigen ausgewählt haben, wenn der Benutzer F1 drückt.  Ein Designer stellt Elementkontext für ein Element ausgewählt in einem Designer, z. B. einer Schaltfläche in einem Formular.  Editoren und Designer müssen an einen Sprachdienst auch beschrieben, wie in [Ältere Sprache Service – Grundlagen](../extensibility/internals/legacy-language-service-essentials.md)herstellen.