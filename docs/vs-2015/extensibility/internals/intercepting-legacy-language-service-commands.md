---
title: Abfangen von Legacy-Sprachdienst Befehlen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6510df2cc9cc1e504f09af033548e0d1c9b4ae74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195009"
---
# <a name="intercepting-legacy-language-service-commands"></a>Abfangen von Befehlen von Legacysprachdiensten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Mit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] können Sie den Sprachdienst Befehle abfangen, die von der Textansicht andernfalls behandelt werden. Dies ist nützlich für sprachspezifisches Verhalten, das von der Textansicht nicht verwaltet wird. Sie können diese Befehle abfangen, indem Sie der Textansicht einen oder mehrere Befehls Filter aus dem Sprachdienst hinzufügen.  
  
## <a name="getting-and-routing-the-command"></a>Erhalten und Weiterleiten des Befehls  
 Ein Befehls Filter ist ein <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Objekt, mit dem bestimmte Zeichensequenzen oder Schlüsselbefehle überwacht werden. Sie können einer einzelnen Textansicht mehrere Befehls Filter zuordnen. Jede Textansicht verwaltet eine Kette von Befehls Filtern. Nachdem Sie einen neuen Befehls Filter erstellt haben, fügen Sie der Kette den Filter für die entsprechende Textansicht hinzu.  
  
 Wenden Sie die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> Methode für den <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> an, um der Kette den Befehls Filter hinzuzufügen. Wenn Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] den Befehl ausführen, gibt einen weiteren Befehls Filter zurück, an den Sie die Befehle übergeben können, die der Befehls Filter nicht behandelt.  
  
 Die folgenden Optionen stehen für die Befehls Behandlung zur Verfügung:  
  
- Behandeln Sie den Befehl, und übergeben Sie dann den Befehl an den nächsten Befehls Filter in der Kette.  
  
- Behandeln Sie den Befehl, und übergeben Sie den Befehl nicht an den nächsten Befehls Filter.  
  
- Behandeln Sie den Befehl nicht, sondern übergeben Sie den Befehl an den nächsten Befehls Filter.  
  
- Ignorieren Sie den Befehl. Behandeln Sie Sie nicht im aktuellen Filter, und übergeben Sie Sie nicht an den nächsten Filter.  
  
  Informationen zu den Befehlen, die ihr Sprachdienst verarbeiten soll, finden Sie unter [wichtige Befehle für Sprachdienst Filter](../../extensibility/internals/important-commands-for-language-service-filters.md).
