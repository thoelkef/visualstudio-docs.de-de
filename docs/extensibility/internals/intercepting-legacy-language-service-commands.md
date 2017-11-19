---
title: Abfangen von Legacy-Dienst Sprachbefehle | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73524ce47dfea2d30e44e51e97bf584a95a86482
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="intercepting-legacy-language-service-commands"></a>Abfangen von Legacy-Dienst Sprachbefehle
Mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], dass Language Service Intercept Befehle, die andernfalls Textansicht behandelt würden. Dies ist hilfreich für sprachspezifisches Verhalten, die der Textansicht nicht verwaltet. Sie können diese Befehle durch Hinzufügen von mindestens -Befehlsfilter anzuzeigende Text aus der Sprachdienst abfangen.  
  
## <a name="getting-and-routing-the-command"></a>Abrufen und den Befehl Routing  
 Ein Befehlsfilter ist ein <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> -Objekt, das bestimmte Zeichensequenzen oder Befehle überwacht. Sie können mehr als ein Befehlsfilter mit einer einzelnen Textzeichenfolge Ansicht zuordnen. Jede Textansicht verwaltet eine Befehlskette Filter. Nachdem Sie einen neuen Befehlsfilter erstellt haben, fügen Sie den Filter auf die Kette für den entsprechenden Text anzeigen.  
  
 Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> Methode für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> die Kette der Befehlsfilter hinzu. Beim Aufruf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gibt einen anderen Befehl Filtern, können Sie die Befehle, die der Befehlsfilter nicht verarbeiten kann übergeben.  
  
 Sie haben die folgenden Optionen für die Befehlsbehandlung von:  
  
-   Der Befehl behandelt, und klicken Sie dann den Befehl an den nächsten Befehlsfilter in der Kette übergeben.  
  
-   Der Befehl behandelt, und übergeben Sie den Befehl an den nächsten Befehlsfilter nicht.  
  
-   Der Befehl nicht behandelt, aber den Befehl an den nächsten Befehlsfilter übergeben.  
  
-   Ignorieren Sie den Befehl. Nicht im aktuellen Filter behandelt, und übergeben Sie ihn nicht an den nächsten Filter.  
  
 Informationen über die Befehle der Sprachdienst behandelt werden sollen, finden Sie unter [wichtige Befehle für Language Service Filter](../../extensibility/internals/important-commands-for-language-service-filters.md).