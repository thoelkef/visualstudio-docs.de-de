---
title: Erstellen benutzerdefinierter Visualisierungen von Daten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.visualizer.troubleshoot
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 50df868f0e01d49d4c49bccae32d743d5291a066
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841184"
---
# <a name="create-custom-visualizers-of-data"></a>Erstellen von benutzerdefinierten Visualisierungen von Daten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visualisierungen sind Komponenten der [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] Debugger-Benutzeroberfläche. Eine schnell *Ansicht erstellt ein* Dialogfeld oder eine andere Schnittstelle, um eine Variable oder ein Objekt auf eine Weise anzuzeigen, die für den Datentyp geeignet ist. So interpretiert zum Beispiel eine HTML-Schnellansicht eine HTML-Zeichenfolge und stellt das Ergebnis so dar, wie es in einem Browserfenster angezeigt würde, eine Bitmapschnellansicht interpretiert eine Bitmapstruktur und zeigt die in der Bitmapdatei enthaltene Grafik an. Bei einigen Schnellansichten können Sie die Daten nicht nur anzeigen lassen, sondern auch bearbeiten.  
  
 Der [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]-Debugger beinhaltet sechs Standardschnellansichten. Dies sind die Schnellansichten für Text, HTML, XML und JSON, die alle auf Zeichenfolgenobjekten basieren, der WPF Tree visualizer (WPF-Strukturschnellansicht) zum Anzeigen der visuellen Struktur eines WPF-Objekts sowie die Datasetschnellansicht, die für die Verarbeitung von DataSet-Objekten, DataView-Objekten und DataTable-Objekten zuständig ist. Weitere Schnellansichten stehen möglicherweise in Zukunft zum Download von der Microsoft Corporation zur Verfügung und werden von Dritten und der Community zur Verfügung. Außerdem können Sie eigene Schnellansichten schreiben und sie im [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]-Debugger installieren.  
  
> [!NOTE]
> In **Store** -apps werden nur die standardmäßigen Text-, HTML-, XML-und JSON-Visualisierungen unterstützt. Benutzerdefinierte (von Benutzern erstellte) Schnellansichten werden nicht unterstützt.  
  
 Schnellansichten werden im Debugger durch ein Lupensymbol dargestellt. Wenn das Lupensymbol in einem **DataTip**, in einem Debuggervariablenfenster oder im Dialogfeld **schnell Überwachung** angezeigt wird, können Sie auf das Lupensymbol klicken, um eine Schnellansicht auszuwählen, die dem Datentyp des entsprechenden Objekts entspricht.  
  
 Schnellansichten werden in Compact Framework nicht unterstützt.  
  
> [!NOTE]
> Debuggerschnellansichten erfordern umfangreichere Privilegien, als sie von einer partiell vertrauenswürdigen Anwendung zugelassen werden. Schnellansichten werden deshalb nicht geladen, wenn die Ausführung in Code mit partieller Vertrauensstellung unterbrochen wurde. Wenn Sie in einer Schnellansicht debuggen möchten, müssen Sie den Code mit voller Vertrauenswürdigkeit ausführen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [How to: Schreiben einer Schnellansicht](../debugger/how-to-write-a-visualizer.md)  
  
 [Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  
  
 [How to: Install a Visualizer (Vorgehensweise: Installieren einer Schnellansicht)](../debugger/how-to-install-a-visualizer.md).  
  
 [Vorgehensweise: Testen und Debuggen einer Schnellansicht](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Referenz zur Schnellansicht-API](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)
