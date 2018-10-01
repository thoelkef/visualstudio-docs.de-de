---
title: Unterstützung von Tools zum Durchsuchen von Symbolen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- symbols, symbol-browsing tools
- browsers, symbol browsers
- symbol-browsing tools
- libraries
- IVsLibrary2 interface, symbol-browsing tools
- IVsSimpleLibrary2 interface, symbol-browsing tools
- symbol-browsing tools, library manager
- symbols
- libraries, symbol-browsing tools
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7c406cdf7b975e37522bccc0d45687593b1a35ac
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512149"
---
# <a name="supporting-symbol-browsing-tools"></a>Unterstützen von Tools zum Durchsuchen von Symbolen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Tools zum Durchsuchen von Symbolen unterstützen](https://docs.microsoft.com/visualstudio/extensibility/internals/supporting-symbol-browsing-tools).  
  
**Objektkatalog**, **Klassenansicht**, **Aufrufbrowser** und **Ergebnisse der Symbolsuche** Tools bieten Symbol Suchfunktionen in Visual Studio. Diese Tools Ansichten der hierarchischen Struktur von Symbolen angezeigt, und die Beziehungen zwischen den Symbolen in der Struktur angezeigt. Die Symbole können Namespaces, Objekte, Klassen, Klassenmembern und anderen Sprachelemente, die in verschiedenen Komponenten enthalten darstellen. Zu den Komponenten zählen Visual Studio-Projekte, externe [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Komponenten und Typbibliotheken (TLB). Weitere Informationen finden Sie unter [Anzeigen der Codestruktur](../../ide/viewing-the-structure-of-code.md).  
  
## <a name="symbol-browsing-libraries"></a>Symbol zum Durchsuchen von Bibliotheken  
 Als eine Sprache-Implementierung können Sie die Funktionen von Visual Studio zum Durchsuchen von Symbolen durch Erstellen von Bibliotheken, die die Symbole in Ihren Komponenten nachverfolgen, und geben Sie die Liste der Symbole auf dem Visual Studio-Objekt-Manager über einen Satz von Schnittstellen erweitern. Eine Bibliothek wird beschrieben, durch die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> Schnittstelle. Der Objekt-Manager für Visual Studio reagiert auf Anforderungen für neue Daten über die Tools zum Durchsuchen von Symbolen durch Abrufen von Daten aus den Bibliotheken und Organisieren sie. Klicken sie anschließend füllt oder aktualisiert die Tools, mit der angeforderten Daten. Abrufen eines Verweises auf die Visual Studio-Objekt-Manager, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, übergeben die <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> -service-ID, die `GetService` Methode.  
  
 Jede Bibliothek muss bei der Visual Studio-Objekt-Manager registrieren, und die Informationen zu allen Bibliotheken zu sammeln. Um eine Bibliothek zu registrieren, rufen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> Methode. Je nachdem, welches Tool die Anforderung initiiert wird wird der Objekt-Manager für Visual Studio sucht die entsprechende Bibliothek und fordert Daten. Die Datenübertragung zwischen den Bibliotheken und die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] -Objekt-Manager in der Liste der Symbole beschrieben, die von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> Schnittstelle.  
  
 Die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] -Objekt-Manager ist verantwortlich für das Aktualisieren in regelmäßigen Abständen von Tools zum Durchsuchen von Symbolen, entsprechend die aktuellen Daten, die in den Bibliotheken enthalten.  
  
 Das folgende Diagramm enthält ein Beispiel für wichtige Elemente, die den Anforderungen/Data Exchange-Prozess zwischen einer Bibliothek und der Objekt-Manager für Visual Studio. Die Schnittstellen in der Abbildung sind Teil einer Anwendung mit verwaltetem Code.  
  
 ![Datenfluss zwischen einer Bibliothek und der Objekt-Manager](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")  
  
 Die Listen von Symbolen, um dem Objekt-Manager von Visual Studio zu bieten, müssen Sie zuerst die Bibliothek mit der Objekt-Manager für Visual Studio registrieren, durch den Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> Methode. Nachdem die Bibliothek registriert wurde, fordert der Objekt-Manager für Visual Studio bestimmte Informationen zu den Funktionen der Bibliothek. Beispielsweise er fordert die Bibliotheksflags und unterstützt Sie durch Aufrufen von Kategorien der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> Methoden. An einem bestimmten Punkt, wenn eines der Tools aus dieser Bibliothek, die Daten anfordert der Objekt-Manager fordert die obersten Ebene Liste von Symbolen durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> Methode. Im Gegenzug die Bibliothek stellt eine Liste von Symbolen und macht es für den Visual Studio-Objekt-Manager über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> Schnittstelle. Die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] -Objekt-Manager bestimmt, wie viele Elemente in der Liste befinden, durch den Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> Methode. Alle folgende Anforderungen beziehen sich auf ein bestimmtes Element in der Liste, und geben die Indexnummer des Elements in jeder Anforderung. Der Visual Studio-Objekt-Manager wird zum Sammeln von Informationen auf den Typ, der Zugriff auf und andere Eigenschaften des Elements durch den Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> Methode.  
  
 Es bestimmt den Namen des Elements durch einen Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> Methode und fordert die Symbolinformationen durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> Methode. Das Symbol auf der linken Seite des Elementnamens angezeigt, und zeigt den Typ des Elements, den Zugriff auf und andere Eigenschaften.  
  
 Die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] -Objekt Manager Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> Methode, um zu bestimmen, ob ein bestimmtes Listenelement erweiterbar und untergeordnete Elemente verfügt. Wenn eine Anforderung an ein Element erweitern UI gesendet werden, fordert der Objekt-Manager die untergeordnete Liste von Symbolen durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> Methode. Der Prozess weiterhin mit verschiedenen Teilen der Struktur, die bei Bedarf erstellt wird.  
  
> [!NOTE]
>  Um einen systemeigenen Code Symbol-Anbieter implementieren, verwenden die <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> Schnittstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Registrieren einer Bibliothek mit der Objekt-Manager](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Vorgehensweise: Verfügbarmachen der Listen von Symbolen, die von der Bibliothek bereitgestellt, der Objekt-Manager](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)   
 [Gewusst wie: Identifizieren von Symbolen in einer Bibliothek](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)

