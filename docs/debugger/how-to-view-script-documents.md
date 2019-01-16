---
title: 'Vorgehensweise: Anzeigen von Skriptdokumenten | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3592056fdde7756f3fbe63d0dc5d86782fdf9a8b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867726"
---
# <a name="how-to-view-script-documents"></a>Vorgehensweise: Anzeigen von Skriptdokumenten
In früheren Versionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wurden clientseitige Skriptdateien, die durch Skripts auf Serverseite generiert wurden, im Fenster Skript-Explorer angezeigt. Da das Fenster Skript-Explorer häufig ausgeblendet war, war die Verfügbarkeit clientseitiger Skripts nicht immer direkt erkennbar.  
  
 In [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] werden clientseitige Skriptdateien, die durch Skripts auf Serverseite generiert wurden, im Projektmappen-Explorer angezeigt, der standardmäßig immer eingeblendet ist. Das Fenster Skript-Explorer wurde entfernt.  
  
 Clientseitige Skriptdateien sind nur sichtbar, wenn Sie sich im Debugmodus oder Unterbrechungsmodus befinden. Sie werden im Knoten **Skriptdokumente** angezeigt.  
  
 Serverseitige Skriptdateien sind immer sichtbar. Sie werden im Knoten **\<Website-Pfadname>** angezeigt. Der Name des Knotens sieht etwa wie in diesem Beispiel aus: `c:\...\Website2\`  
  
### <a name="to-view-a-server-side-script-document"></a>So zeigen Sie ein serverseitiges Skriptdokument an  
  
1.  Öffnen Sie im **Projektmappen-Explorer** den Knoten **\<Website-Pfadname>**.  
  
2.  Doppelklicken Sie auf die Skriptdatei, die Sie anzeigen möchten.  
  
     Die serverseitige Skriptdatei wird in einem Quellcodefenster geöffnet.  
  
### <a name="to-view-a-client-side-script-document"></a>So zeigen Sie ein clientseitiges Skriptdokument an  
  
1.  Öffnen Sie im **Projektmappen-Explorer** den Knoten **Skriptdokumente**.  
  
2.  Doppelklicken Sie auf die Skriptdatei, die Sie anzeigen möchten.  
  
     Die clientseitige Skriptdatei wird in einem Quellcodefenster geöffnet.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)