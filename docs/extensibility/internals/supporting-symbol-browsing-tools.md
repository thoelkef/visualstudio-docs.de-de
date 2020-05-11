---
title: Unterstützung von Symbol-Browsing-Tools | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4998e47ccd6f99df2710833c18975d57e3bb92f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704766"
---
# <a name="supporting-symbol-browsing-tools"></a>Unterstützen von Tools zum Durchsuchen von Symbolen
**Objektbrowser**, **Klassenansicht**, **Aufrufbrowser** und **Symbolergebnisse suchen** Tools bieten Symbol-Browsing-Funktionen in Visual Studio. Diese Werkzeuge zeigen hierarchische Baumansichten von Symbolen und die Beziehungen zwischen den Symbolen in der Struktur an. Die Symbole können Namespaces, Objekte, Klassen, Klassenmember und andere Sprachelemente darstellen, die in verschiedenen Komponenten enthalten sind. Zu den Komponenten gehören Visual Studio-Projekte, externe .NET Framework-Komponenten und Typbibliotheken (.tlb). Weitere Informationen finden Sie unter [Anzeigen der Codestruktur](../../ide/viewing-the-structure-of-code.md).

## <a name="symbol-browsing-libraries"></a>Symbol-Browsing-Bibliotheken
 Als Sprachimplementierer können Sie die Visual Studio-Symbol-Browsing-Funktionen erweitern, indem Sie Bibliotheken erstellen, die die Symbole in Ihren Komponenten nachverfolgen und die Symbolelisten für den Visual Studio-Objekt-Manager über eine Reihe von Schnittstellen bereitstellen. Eine Bibliothek wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> von der Schnittstelle beschrieben. Der Visual Studio-Objekt-Manager reagiert auf Anforderungen nach neuen Daten aus den Symbol-Browsing-Tools, indem er die Daten aus den Bibliotheken abruft und organisiert. Anschließend werden die Tools mit den angeforderten Daten aufgepopt oder aktualisiert. Um einen Verweis auf den Visual <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>Studio-Objekt-Manager abzuerhalten, übergeben Sie die <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> Dienst-ID an die `GetService` Methode.

 Jede Bibliothek muss sich beim Visual Studio-Objekt-Manager registrieren, der die Informationen für alle Bibliotheken sammelt. Um eine Bibliothek zu <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> registrieren, rufen Sie die Methode auf. Je nachdem, welches Tool die Anforderung initiiert, sucht der Visual Studio-Objekt-Manager die entsprechende Bibliothek und fordert Daten an. Die Daten werden in Listen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] von Symbolen, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> von der Schnittstelle beschrieben werden, zwischen den Bibliotheken und dem Objektmanager geleitet.

 Der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Objekt-Manager ist für das regelmäßige Aktualisieren von Symbol-Browsing-Tools verantwortlich, um die aktuellsten Daten in den Bibliotheken widerzuspiegeln.

 Das folgende Diagramm enthält ein Beispiel für Schlüsselelemente des Anforderungen/Datenaustauschprozesses zwischen einer Bibliothek und dem Visual Studio-Objekt-Manager. Die Schnittstellen im Diagramm sind Teil einer verwalteten Codeanwendung.

 ![Datenfluss zwischen einer Bibliothek und dem Objekt-Manager](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagramm")

 Um die Symbollisten für den Visual Studio-Objekt-Manager bereitzustellen, müssen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> Bibliothek zuerst beim Visual Studio-Objekt-Manager registrieren, indem Sie die Methode aufrufen. Nachdem die Bibliothek registriert wurde, fordert der Visual Studio-Objektmanager bestimmte Informationen zu den Funktionen der Bibliothek an. Beispielsweise werden die Bibliotheksflags und unterstützten <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> Kategorien durch Aufrufen der und -methoden angefordert. Irgendwann, wenn eines der Tools Daten aus dieser Bibliothek anfordert, fordert der Objekt-Manager die Liste der Symbole der obersten Ebene an, indem er die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> Methode aufruft. Als Antwort erstellt die Bibliothek eine Liste von Symbolen und macht <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> sie über die Schnittstelle für den Visual Studio-Objekt-Manager verfügbar. Der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Objekt-Manager bestimmt, wie viele Elemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> in der Liste sind, indem er die Methode aufruft. Alle folgenden Anforderungen beziehen sich auf ein bestimmtes Element in der Liste und geben die Artikelindexnummer in jeder Anforderung ein. Der Visual Studio-Objekt-Manager sammelt die Informationen über den Typ, die Barrierefreiheit <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> und andere Eigenschaften des Elements durch Aufrufen der Methode.

 Der Name des Elements wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> durch Aufrufen der Methode bestimmt <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> und die Symbolinformationen durch Aufrufen der Methode anfordert. Das Symbol wird links neben dem Elementnamen angezeigt und zeigt den Typ des Elements, die Barrierefreiheit und andere Eigenschaften an.

 Der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Objekt-Manager <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> ruft die Methode auf, um zu bestimmen, ob ein bestimmtes Listenelement erweiterbar ist und untergeordnete Elemente enthält. Wenn die Benutzeroberfläche eine Anforderung zum Erweitern eines Elements sendet, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> fordert der Objekt-Manager die untergeordnete Liste der Symbole an, indem er die Methode aufruft. Der Prozess wird fortgesetzt, wobei verschiedene Teile des Baumes bei Bedarf gebaut werden.

> [!NOTE]
> Um einen systemeigenen Codesymbolanbieter <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> zu implementieren, verwenden Sie die und Schnittstellen.

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Registrieren einer Bibliothek beim Objekt-Manager](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Gewusst wie: Verfügbarmachen der Listen von Symbolen, die von der Bibliothek für den Objekt-Manager bereitgestellt werden](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [Gewusst wie: Identifizieren von Symbolen in einer Bibliothek](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)
