---
title: Erstellen benutzerdefinierter Schnellansichten von Daten | Microsoft-Dokumentation
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
ms.openlocfilehash: f890277190b9b4d28873e1fe394abdcd95b8a3a6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947602"
---
# <a name="create-custom-visualizers-of-data"></a>Erstellen Sie benutzerdefinierter Schnellansichten von Daten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Schnellansichten sind Komponenten der [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] Debugger-Benutzeroberfläche. Ein *Schnellansicht* erstellt ein Dialogfeld oder eine andere Schnittstelle für eine Variable oder ein Objekt in einer Weise anzeigen, die für den Datentyp geeignet ist. So interpretiert zum Beispiel eine HTML-Schnellansicht eine HTML-Zeichenfolge und stellt das Ergebnis so dar, wie es in einem Browserfenster angezeigt würde, eine Bitmapschnellansicht interpretiert eine Bitmapstruktur und zeigt die in der Bitmapdatei enthaltene Grafik an. Bei einigen Schnellansichten können Sie die Daten nicht nur anzeigen lassen, sondern auch bearbeiten.  
  
 Der [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]-Debugger beinhaltet sechs Standardschnellansichten. Dies sind der Text, HTML, XML und JSON-Schnellansichten, die alle auf Zeichenfolgenobjekten arbeiten. die WPF-Strukturschnellansicht zum Anzeigen der visuellen Struktur eines WPF-Objekt; sowie die Datasetschnellansicht, die für die DataView-DataSet und DataTable-Objekten funktioniert. Weitere Schnellansichten stehen möglicherweise in Zukunft zum Download von der Microsoft Corporation zur Verfügung und werden von Dritten und der Community zur Verfügung. Außerdem können Sie eigene Schnellansichten schreiben und sie im [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]-Debugger installieren.  
  
> [!NOTE]
>  In **Store** apps, die nur den Standardtext, HTML, XML und JSON-Schnellansichten werden unterstützt. Benutzerdefinierte (von Benutzern erstellte) Schnellansichten werden nicht unterstützt.  
  
 Schnellansichten werden im Debugger durch ein Lupensymbol dargestellt. Wenn Sie das Lupensymbol in sehen eine **DataTip**, in einem Debuggervariablenfenster oder in der **Schnellüberwachung** Dialogfeld klicken Sie auf das Lupensymbol, um eine dem Datentyp entsprechende Schnellansicht auszuwählen des entsprechenden Objekts.  
  
 Schnellansichten werden in Compact Framework nicht unterstützt.  
  
> [!NOTE]
>  Debuggerschnellansichten erfordern umfangreichere Privilegien, als sie von einer partiell vertrauenswürdigen Anwendung zugelassen werden. Schnellansichten werden deshalb nicht geladen, wenn die Ausführung in Code mit partieller Vertrauensstellung unterbrochen wurde. Wenn Sie in einer Schnellansicht debuggen möchten, müssen Sie den Code mit voller Vertrauenswürdigkeit ausführen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Vorgehensweise: Schreiben einer Schnellansicht](../debugger/how-to-write-a-visualizer.md)  
  
 [Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  
  
 [Vorgehensweise: Install a Visualizer (Vorgehensweise: Installieren einer Schnellansicht)](../debugger/how-to-install-a-visualizer.md).  
  
 [Vorgehensweise: Testen und Debuggen einer Schnellansicht](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Referenz zur Schnellansicht-API](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)
