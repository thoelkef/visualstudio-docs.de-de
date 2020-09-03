---
title: 'Vorgehensweise: Anzeigen von Skriptdokumenten | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 88f923ab0447f1ac7d57e84d94f0ab442d912d67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189603"
---
# <a name="how-to-view-script-documents"></a>Gewusst wie: Anzeigen von Skriptdokumenten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In früheren Versionen von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wurden clientseitige Skriptdateien, die durch Skripts auf Serverseite generiert wurden, im Fenster Skript-Explorer angezeigt. Da das Fenster Skript-Explorer häufig ausgeblendet war, war die Verfügbarkeit clientseitiger Skripts nicht immer direkt erkennbar.  
  
 In [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] werden clientseitige Skriptdateien, die durch Skripts auf Serverseite generiert wurden, im Projektmappen-Explorer angezeigt, der standardmäßig immer eingeblendet ist. Das Fenster Skript-Explorer wurde entfernt.  
  
 Clientseitige Skriptdateien sind nur sichtbar, wenn Sie sich im Debugmodus oder Unterbrechungsmodus befinden. Sie werden im Knoten **Skriptdokumente** angezeigt.  
  
 Serverseitige Skriptdateien sind immer sichtbar. Sie werden im- **\<Website Pathname>** Knoten angezeigt. Der Name des Knotens ähnelt dem folgenden Beispiel: `c:\...\Website2\`  
  
### <a name="to-view-a-server-side-script-document"></a>So zeigen Sie ein serverseitiges Skriptdokument an  
  
1. Öffnen Sie im **Projektmappen-Explorer** den Knoten **\<Website Pathname>** .  
  
2. Doppelklicken Sie auf die Skriptdatei, die Sie anzeigen möchten.  
  
     Die serverseitige Skriptdatei wird in einem Quellcodefenster geöffnet.  
  
### <a name="to-view-a-client-side-script-document"></a>So zeigen Sie ein clientseitiges Skriptdokument an  
  
1. Öffnen Sie im **Projektmappen-Explorer** den Knoten **Skriptdokumente**.  
  
2. Doppelklicken Sie auf die Skriptdatei, die Sie anzeigen möchten.  
  
     Die clientseitige Skriptdatei wird in einem Quellcodefenster geöffnet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)
