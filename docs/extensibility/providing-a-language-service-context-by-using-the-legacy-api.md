---
title: Bereitstellen von Language Dienstkontext über die Legacy-API | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3556fcce3d14d5069854c64d81cb780123a979d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140071"
---
# <a name="providing-a-language-service-context-by-using-the-legacy-api"></a>Bereitstellen von Language Dienstkontext über die Legacy-API
Es gibt zwei Optionen für einen Sprachdienst Benutzer Kontext mit Bereitstellen der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Core-Editor: Text Marker Kontext bereitzustellen, oder geben Sie alle Benutzerkontext. Hier werden die Unterschiede zwischen den einzelnen beschrieben.  
  
 Weitere Informationen zum Bereitstellen von Kontext, um einen Sprachdienst, die mit Ihren eigenen Editor verbunden ist, finden Sie unter [Vorgehensweise: Bereitstellen von Kontext für Editoren](../extensibility/how-to-provide-context-for-editors.md).  
  
## <a name="provide-text-marker-context-to-the-editor"></a>Geben Sie Text Marker Kontext auf den Editor  
 Compilerfehler erkennbar Text Marker im Kontext bereit der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Haupt-Editor, implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> Schnittstelle. In diesem Szenario stellt der Sprachdienst Kontext aus, nur, wenn der Cursor in einen Text-Marker befindet. Dadurch wird den Editor das Schlüsselwort an der Cursorposition zum Bereitstellen der **dynamische Hilfe** Fenster keine Attribute.  
  
## <a name="provide-all-user-context-to-the-editor"></a>Geben Sie alle Benutzerkontext auf dem Editor  
 Wenn Sie einen Sprachdienst erstellen und Verwenden der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] core-Editor, und klicken Sie dann die Sie implementieren können, die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> Schnittstelle, um Kontext für den Sprachdienst bereitzustellen.  
  
 Für die Implementierung von `IVsLanguageContextProvider`, eine Kontextsammlung (Auflistung) angefügt ist, auf den Editor, der für die Aktualisierung Kontext Behälter verantwortlich ist. Wenn die **dynamische Hilfe** Fenster Aufrufe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> Schnittstelle in diesem Kontext Behälter während der Leerlaufzeit Kontext Behälter fragt den Editor für ein Update. Der Editor benachrichtigt dann dem Sprachdienst sollten Editor aktualisieren, und übergibt einen Zeiger auf den Kontext Eigenschaftenbehälters. Dies erfolgt durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> Methode aus dem Editor, um der Sprachdienst. Verwenden den Mauszeiger, um Kontext Behälter, kann der Sprachdienst jetzt hinzufügen und entfernen Attribute und Schlüsselwörter. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>.  
  
 Es gibt zwei verschiedene Möglichkeiten zur Implementierung `IVsLanguageContextProvider`:  
  
-   Geben Sie ein Schlüsselwort, um den Kontext Eigenschaftenbehälters.  
  
     Wenn der Editor zum Aktualisieren der Behälter Kontext aufgerufen wird, übergeben Sie die geeignete Schlüsselwörter und Attribute und wieder `S_OK`. Dieser Rückgabewert weist den Editor zum Beibehalten des Kontexts-Schlüsselwort und Attribut, sondern geben Sie das Schlüsselwort an der Cursorposition zum Kontext Behälter.  
  
-   Das Schlüsselwort aus das Schlüsselwort an der Cursorposition abrufen  
  
     Wenn der Editor zum Aktualisieren der Behälter Kontext aufgerufen wird, übergeben Sie die entsprechenden Attribute und wieder `E_FAIL`. Dieser Rückgabewert wird angewiesen, den Editor, um die Attribute im Behälter Kontext beibehalten, aber Kontext Behälter mit dem Schlüsselwort an der Cursorposition zu aktualisieren.  
  
 Das folgende Diagramm veranschaulicht, wie der Kontext für einen Sprachdienst bereitgestellt wird, die implementiert `IVsLanguageContextProvider`.  
  
 ![Grafik zu LangServiceImplementation2](../extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
Kontext für einen Sprachdienst  
  
 Siehe das Diagramm die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Core Text-Editor verfügt über einen Kontext Behälter angefügt ist. Dieser Kontext Behälter verweist auf drei separaten Unterkontext aus diesem: Sprachdienst, Standard-Editor und einem Text-Marker. Die Language-Dienst und Text Marker Unterkontext aus diesem enthalten Attribute und Schlüsselwörter für den Sprachdienst, wenn die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> Schnittstelle wird implementiert, und Text-Marker Wenn die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> Schnittstelle implementiert wird. Wenn Sie nicht eine der folgenden Schnittstellen implementieren, stellt der Editor Kontext für das Schlüsselwort an der Cursorposition im Standard-Editor Unterkontext Behälter bereit.  
  
## <a name="context-guidelines-for-editors-and-designers"></a>Kontext-Richtlinien für die Editoren und Designern  
 Designer und Editoren müssen für den Editor oder Designer-Fenster ein allgemeines Schlüsselwort angeben. Dies erfolgt, damit ein Hilfethema generische jedoch gegebenenfalls für den Designer oder Editor angezeigt wird, wenn ein Benutzer F1 drückt. Einen Editor muss darüber hinaus geben die aktuellen Schlüsselworts an der Cursorposition oder geben Sie eine wesentliche Begriffe, die basierend auf der aktuellen Auswahl. Dies erfolgt, um sicherzustellen, dass ein Hilfethema für den Text oder UI-Element gezeigt wird, oder zeigt ausgewählt, wenn der Benutzer F1 drückt. Ein Designer stellt Kontext für ein Element in einem Designer, z. B. eine Schaltfläche in einem Formular ausgewählt. Editoren und Designern müssen auch eine Verbindung herstellen, einen Sprachdienst im [Legacy Language Service Essentials](../extensibility/internals/legacy-language-service-essentials.md).