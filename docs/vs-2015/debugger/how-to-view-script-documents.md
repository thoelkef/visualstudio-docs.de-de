---
title: 'Vorgehensweise: Anzeigen von Skriptdokumenten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc24c5e9c2332516cbf939e14581a2df7bea44eb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520844"
---
# <a name="how-to-view-script-documents"></a>Gewusst wie: Anzeigen von Skriptdokumenten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Anzeigen von Skriptdokumenten](https://docs.microsoft.com/visualstudio/debugger/how-to-view-script-documents).  
  
In früheren Versionen von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wurden clientseitige Skriptdateien, die durch Skripts auf Serverseite generiert wurden, im Fenster Skript-Explorer angezeigt. Da das Fenster Skript-Explorer häufig ausgeblendet war, war die Verfügbarkeit clientseitiger Skripts nicht immer direkt erkennbar.  
  
 In [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] werden clientseitige Skriptdateien, die durch Skripts auf Serverseite generiert wurden, im Projektmappen-Explorer angezeigt, der standardmäßig immer eingeblendet ist. Das Fenster Skript-Explorer wurde entfernt.  
  
 Clientseitige Skriptdateien sind nur sichtbar, wenn Sie sich im Debugmodus oder Unterbrechungsmodus befinden. Sie werden in der **Skriptdokumente** Knoten.  
  
 Serverseitige Skriptdateien sind immer sichtbar. Sie werden in der  **\<Website-Pfadname >** Knoten. Der Name des Knotens sieht etwa wie in diesem Beispiel aus: `c:\...\Website2\`  
  
### <a name="to-view-a-server-side-script-document"></a>So zeigen Sie ein serverseitiges Skriptdokument an  
  
1.  In **Projektmappen-Explorer**öffnen die  **\<Website-Pfadname >** Knoten.  
  
2.  Doppelklicken Sie auf die Skriptdatei, die Sie anzeigen möchten.  
  
     Die serverseitige Skriptdatei wird in einem Quellcodefenster geöffnet.  
  
### <a name="to-view-a-client-side-script-document"></a>So zeigen Sie ein clientseitiges Skriptdokument an  
  
1.  In **Projektmappen-Explorer**öffnen die **Skriptdokumente** Knoten.  
  
2.  Doppelklicken Sie auf die Skriptdatei, die Sie anzeigen möchten.  
  
     Die clientseitige Skriptdatei wird in einem Quellcodefenster geöffnet.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)



