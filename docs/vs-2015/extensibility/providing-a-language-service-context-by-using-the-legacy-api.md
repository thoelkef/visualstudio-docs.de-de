---
title: Bereitstellen eines Sprachdienst Kontexts mithilfe der Legacy-API | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4471b71b612008ba7d0733c92286415cd3c3f6b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193867"
---
# <a name="providing-a-language-service-context-by-using-the-legacy-api"></a>Bereitstellen eines Sprachdienstkontexts mithilfe der Legacy-API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Es gibt zwei Optionen für einen Sprachdienst zum Bereitstellen des Benutzer Kontexts mithilfe des [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Kern Editors: Text markerkontext bereitstellen oder gesamten Benutzer Kontext bereitstellen. Die Unterschiede zwischen den einzelnen werden hier beschrieben.  
  
 Weitere Informationen zum Bereitstellen von Kontext für einen Sprachdienst, der mit Ihrem eigenen Editor verbunden ist, finden Sie unter Gewusst [wie: Bereitstellen von Kontext für Editoren](../extensibility/how-to-provide-context-for-editors.md).  
  
## <a name="provide-text-marker-context-to-the-editor"></a>Text markerkontext für den Editor angeben  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Implementieren Sie die-Schnittstelle, um Kontext für Compilerfehler bereitzustellen, die durch Textmarker im Kern-Editor angegeben werden <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> . In diesem Szenario stellt der Sprachdienst nur dann Kontext bereit, wenn sich der Cursor auf einem Textmarker befindet. Dies ermöglicht es dem Editor, das-Schlüsselwort am Cursor für das **Dynamische Hilfe** Fenster ohne Attribute bereitzustellen.  
  
## <a name="provide-all-user-context-to-the-editor"></a>Allen Benutzer Kontext für den Editor bereitstellen  
 Wenn Sie einen Sprachdienst erstellen und den [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Kern-Editor verwenden, können Sie die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> Schnittstelle implementieren, um Kontext für Ihren Sprachdienst bereitzustellen.  
  
 Für die Implementierung von `IVsLanguageContextProvider` wird ein Kontext Behälter (Collection) an den Editor angefügt, der für das Aktualisieren des Kontext Behälters zuständig ist. Wenn das **Dynamische Hilfe** Fenster die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> Schnittstelle in diesem Kontext Behälter zur Leerlaufzeit aufruft, fragt der Kontext Behälter den Editor nach einem Update ab. Der Editor benachrichtigt den Sprachdienst dann, dass er den Editor aktualisieren soll, und übergibt einen Zeiger an den Kontext Behälter. Dies erfolgt durch Aufrufen der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> Methode aus dem Editor für den Sprachdienst. Mithilfe des Zeigers auf den Kontext Behälter kann der Sprachdienst nun Attribute und Schlüsselwörter hinzufügen und entfernen. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>.  
  
 Es gibt zwei verschiedene Möglichkeiten, um zu implementieren `IVsLanguageContextProvider` :  
  
- Angeben eines Schlüssel Worts für den Kontext Behälter  
  
   Wenn der Editor aufgerufen wird, um den Kontext Behälter zu aktualisieren, übergeben Sie die entsprechenden Schlüsselwörter und Attribute, und geben Sie dann zurück `S_OK` . Dieser Rückgabewert weist den Editor an, das Schlüsselwort und den Attribut Kontext beizubehalten, anstatt das Schlüsselwort am Cursor für den Kontext Behälter bereitzustellen.  
  
- Abrufen des Schlüssel Worts aus dem Schlüsselwort am Cursor  
  
   Wenn der Editor aufgerufen wird, um den Kontext Behälter zu aktualisieren, übergeben Sie die entsprechenden Attribute, und geben Sie dann zurück `E_FAIL` . Dieser Rückgabewert weist den Editor an, die Attribute im Kontext Behälter beizubehalten, aktualisiert jedoch den Kontext Behälter mit dem Schlüsselwort am Cursor.  
  
  Im folgenden Diagramm wird veranschaulicht, wie der Kontext für einen Sprachdienst bereitgestellt wird, der implementiert `IVsLanguageContextProvider` .  
  
  ![Grafik zu LangServiceImplementation2](../extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
  Kontext für einen Sprachdienst  
  
  Wie Sie im Diagramm sehen können, ist dem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Core-Text-Editor ein Kontext Behälter angefügt. Diese Kontext Sammlung verweist auf drei separate unter Kontext Behälter: Sprachdienst, Standard-Editor und Textmarker. Die unter Kontext Behälter Sprachdienst und Textmarker enthalten Attribute und Schlüsselwörter für den Sprachdienst, wenn die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> Schnittstelle implementiert ist, und Textmarker, wenn die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> Schnittstelle implementiert ist. Wenn Sie keine dieser Schnittstellen implementieren, stellt der Editor den Kontext für das Schlüsselwort am Cursor im unter Kontext Behälter des Standard-Editors bereit.  
  
## <a name="context-guidelines-for-editors-and-designers"></a>Kontext Richtlinien für Editoren und Designer  
 Designer und Editoren müssen ein allgemeines Schlüsselwort für den Editor oder das Designer Fenster bereitstellen. Dies geschieht, damit ein generisches, aber geeignetes Hilfethema für den Designer oder den Editor angezeigt wird, wenn ein Benutzer F1 drückt. Zusätzlich muss ein Editor das aktuelle Schlüsselwort am Cursor angeben oder einen Schlüsselbegriff basierend auf der aktuellen Auswahl angeben. Dadurch wird sichergestellt, dass ein Hilfethema für den Text oder das UI-Element, auf das bzw. das verwiesen wird, angezeigt wird, wenn der Benutzer F1 drückt. Ein Designer liefert Kontext für ein Element, das in einem Designer ausgewählt ist, z. b. eine Schaltfläche in einem Formular. Editoren und Designer müssen auch eine Verbindung mit einem Sprachdienst herstellen, wie in [Legacy Language Service Essentials](../extensibility/internals/legacy-language-service-essentials.md)beschrieben.
