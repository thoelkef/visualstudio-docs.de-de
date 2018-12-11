---
title: 'Vorgehensweise: Anzeigen von Skriptdokumenten | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 5bfa273f98cebdf61f865e03a02c9b2d5f22bfa9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474728"
---
# <a name="how-to-view-script-documents"></a>Gewusst wie: Anzeigen von Skriptdokumenten
In früheren Versionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wurden clientseitige Skriptdateien, die durch Skripts auf Serverseite generiert wurden, im Fenster Skript-Explorer angezeigt. Da das Fenster Skript-Explorer häufig ausgeblendet war, war die Verfügbarkeit clientseitiger Skripts nicht immer direkt erkennbar.  
  
 In [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] werden clientseitige Skriptdateien, die durch Skripts auf Serverseite generiert wurden, im Projektmappen-Explorer angezeigt, der standardmäßig immer eingeblendet ist. Das Fenster Skript-Explorer wurde entfernt.  
  
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