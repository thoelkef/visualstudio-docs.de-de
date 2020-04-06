---
title: Abfangen von Legacy Language Service-Befehlen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5206bced8b4bfae32498434765e5c3f61801b386
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707451"
---
# <a name="intercepting-legacy-language-service-commands"></a>Abfangen von Befehlen von Legacysprachdiensten
Mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]können Sie den Sprachdienst Befehle abfangen lassen, die die Textansicht andernfalls verarbeiten würde. Dies ist nützlich für sprachspezifisches Verhalten, das in der Textansicht nicht verwaltet wird. Sie können diese Befehle abfangen, indem Sie der Textansicht aus dem Sprachdienst einen oder mehrere Befehlsfilter hinzufügen.

## <a name="getting-and-routing-the-command"></a>Abrufen und Routing des Befehls
 Ein Befehlsfilter <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ist ein Objekt, das bestimmte Zeichensequenzen oder Tastenbefehle überwacht. Sie können mehr als einen Befehlsfilter einer einzelnen Textansicht zuordnen. Jede Textansicht verwaltet eine Kette von Befehlsfiltern. Nachdem Sie einen neuen Befehlsfilter erstellt haben, fügen Sie den Filter der Kette für die entsprechende Textansicht hinzu.

 Rufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Methode auf der auf, um den Befehlsfilter zur Kette hinzuzufügen. Wenn Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aufrufen, gibt ein weiterer Befehlsfilter zurück, an den Sie die Befehle übergeben können, die der Befehlsfilter nicht verarbeitet.

 Sie haben die folgenden Optionen für die Befehlsbehandlung:

- Behandeln Sie den Befehl, und übergeben Sie den Befehl dann an den nächsten Befehlsfilter in der Kette.

- Behandeln Sie den Befehl, und übergeben Sie den Befehl nicht an den nächsten Befehlsfilter.

- Behandeln Sie den Befehl nicht, übergeben Sie den Befehl jedoch an den nächsten Befehlsfilter.

- Ignorieren Sie den Befehl. Behandeln Sie sie nicht im aktuellen Filter, und geben Sie sie nicht an den nächsten Filter weiter.

  Informationen zu den Befehlen, die Ihr Sprachdienst verarbeiten soll, finden Sie unter [Wichtige Befehle für Sprachdienstfilter](../../extensibility/internals/important-commands-for-language-service-filters.md).
