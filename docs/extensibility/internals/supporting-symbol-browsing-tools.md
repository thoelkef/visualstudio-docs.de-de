---
title: "Unterst&#252;tzung von Tools zum Durchsuchen des Symbols | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Symbole, Tools zum Durchsuchen des Symbols"
  - "Browser, Symbol-Browser"
  - "Tools zum Durchsuchen des Symbols"
  - "Bibliotheken"
  - "Tools zum Durchsuchen des Symbols IVsLibrary2-Schnittstelle"
  - "Tools zum Durchsuchen des Symbols IVsSimpleLibrary2-Schnittstelle"
  - "Tools zum Durchsuchen des Symbols, Bibliotheks-manager"
  - "Symbole"
  - "Tools zum Durchsuchen von Symbol-Bibliotheken"
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# Unterst&#252;tzung von Tools zum Durchsuchen des Symbols
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

**Objektkatalog**, **Klassenansicht**, **Aufrufbrowser** und **Ergebnisse der Symbolsuche** Tools bieten Funktionen in Visual Studio Symbol suchen.  Diese Tools sind hierarchische Strukturansichten von Symbolen an, und zeigen die Beziehungen zwischen den Symbolen in der Struktur an.  Die Symbole können Namespaces, Klassen, Objekten und andere Klassenmember Sprachelemente in den verschiedenen Komponenten enthalten sind.  Die Komponenten schließen Visual Studio\-Projekten, [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] die externe Komponenten und Bibliotheken des Typs \(.tlb\).  Weitere Informationen finden Sie unter [Anzeigen der Codestruktur](../../ide/viewing-the-structure-of-code.md).  
  
## Symbol\-Durchsuchen Bibliotheken  
 Bei Programmiersprachen von Visual Studio können Sie die Implementierung des Symbols Durchsuchen Funktionen erweitern, indem Sie Bibliotheken erstellen, die die Symbole in Komponenten nachverfolgen und Listen von Symbolen in Visual Studio\-Objekt Manager durch eine Gruppe von Schnittstellen bereitstellen.  Eine Bibliothek wird durch die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2>\-Schnittstelle beschrieben.  Der Visual Studio\-Objekt Manager reagiert auf Anforderung für neue Daten aus dem Symbol Tools zum Durchsuchen von Daten, indem er die Bibliotheken erhält und organisiert.  Sie wird anschließend nach oben oder aktualisiert die Tools mit den angeforderten Daten.  Zum Abrufen eines Verweises auf Visual Studio\-Objekt Manager, führen <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, die <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> Dienst ID zur `GetService`\-Methode.  
  
 Jede Bibliothek muss mit dem Visual Studio\-Objekt Manager registrieren, die die Informationen über alle Bibliotheken erfasst.  Um eine Bibliothek zu registrieren, rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>\-Methode veranschaulicht.  Je nachdem, welches Tool die Anforderung initiiert, sucht der Visual Studio\-Objekt Manager die entsprechende Bibliothek und fordert Daten.  Die Daten zwischen durchläuft die Bibliotheken und den Manager [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Objekt in Listen von Symbolen, die von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>\-Schnittstelle beschrieben werden.  
  
 Der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Objekt Manager ist für Symbol Durchsuchen Tools in regelmäßigen Abständen aktualisieren, um die aktuellsten Daten widerzuspiegeln, die in Bibliotheken enthalten sind.  
  
 Das folgende Diagramm enthält ein Beispiel für Schlüsselelementen des Anforderung\/Datenaustausch Prozesses zwischen einer Bibliothek und dem Visual Studio\-Objekt Manager.  Die Schnittstellen im Diagramm sind Teil einer verwalteten Code\-Anwendung.  
  
 ![Datenfluss zwischen einer Bibliothek und dem Objekt&#45;Manager](~/docs/extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")  
  
 Um die Liste der Symbole in Visual Studio\-Objekt Manager bereitzustellen, müssen Sie die Bibliothek mit dem Visual Studio\-Objekt Manager registrieren zunächst mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>\-Methode aufrufen.  Nachdem die Bibliothek registriert ist, benötigt der Visual Studio\-Objekt Manager spezifische Informationen über die Funktionen der Bibliothek an.  Zum Beispiel aufgerufen und Flags für die Bibliothek die unterstützten Kategorien, indem die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A>\-Methoden aufgerufen werden.  So fügen Sie einem bestimmten Zeitpunkt wenn eines der Tools Daten aus dieser Bibliothek erfordert, fordert der Objekt Manager um die Liste der obersten Ebene von Symbolen, indem er die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A>\-Methode aufgerufen wird.  Daraufhin stellt die Bibliothek eine Liste von Symbolen und fügt sie dem Visual Studio\-Objekt Manager durch die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>\-Schnittstelle aus.  Der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Objekt Manager bestimmt, wie viele Elemente in der Liste enthalten sind, indem Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A>\-Methode aufrufen.  Alle nachfolgenden Anforderungen verknüpfen zu einem angegebenen Element in der Liste, und geben die indexnummer Element in jeder Anforderung.  Der Visual Studio\-Objekt Manager verwendet weiterhin die Informationen über den Typ, der Barrierefreiheit sowie andere Eigenschaften des Elements zu sammeln, indem er die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A>\-Methode aufgerufen wird.  
  
 Sie bestimmt den Namen des Elements, indem sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A>\-Methode aufrufen und fordert die Symbolinformationen auf, indem sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A>\-Methode aufrufen.  Das Symbol wird an der linken Seite des Elementnamens angezeigt und den Typ des Elements, der Barrierefreiheit sowie die Werte weiterer Eigenschaften darstellt.  
  
 Der Manager [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\-Objekt ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A>\-Methode auf, um zu bestimmen, ob ein angegebenes Listenelement erweiterbar ist und über untergeordnete Elemente verfügt.  Wenn der Benutzeroberfläche eine Anforderung sendet, ein Element zu erweitern, fordert der Objekt Manager um die untergeordnete Liste von Symbolen, indem er die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A>\-Methode aufgerufen wird.  Der Prozess wird mit verschiedenen Teilen der Struktur fortgesetzt, die bei Bedarf erstellt wird.  
  
> [!NOTE]
>  Um einen systemeigenen Schlüsselsymbol Textanbieter zu implementieren, verwenden Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2>\-Schnittstellen.  
  
## Siehe auch  
 [Gewusst wie: Registrieren eine Bibliothek mit der Objekt\-Manager](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Gewusst wie: Listen von Symbolen, die von der Bibliothek bereitgestellt, der Objekt\-Manager verfügbar machen](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)   
 [Gewusst wie: Identifizieren von Objekten in einer Bibliothek](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)