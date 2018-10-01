---
title: 'Vorgehensweise: Serialisieren von Symbolinformationen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 04bce9383142ee6916fa7ade50feda072019f530
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520821"
---
# <a name="how-to-serialize-symbol-information"></a>Gewusst wie: Serialisieren von Symbolinformationen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Serialisieren von Symbolinformationen](https://docs.microsoft.com/visualstudio/profiling/how-to-serialize-symbol-information).  
  
Sie können Symbole serialisieren, die zum Analysieren Ihrer Anwendung erforderlich sind. Die Serialisierung von Symbolen fügt Symbole in die VSP-Datei ein. Durch das Einfügen von Symbolinformationen in die VSP-Datei können andere Personen einen Leistungsbericht analysieren, ohne Zugriff auf die Originalsymbole zu haben. Wenn Symbole nicht serialisiert werden, müssen Sie die instrumentierte EXE- und PDB-Dateien zum Analysieren der VSP-Datei haben.  
  
### <a name="to-automatically-serialize-symbol-information"></a>So serialisieren Sie automatisch Symbolinformationen  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
     Das Dialogfeld **Optionen** wird angezeigt.  
  
2.  Klicken Sie auf **Leistungstools**.  
  
3.  Wählen Sie unter **Allgemeine Einstellungen** **Symbolinformationen automatisch serialisieren** aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)   
 [Vorgehensweise: Verweisen auf Windows-Symbolinformationen](../profiling/how-to-reference-windows-symbol-information.md)   
 [Vorgehensweise: Speichern von analysierten Berichten](http://msdn.microsoft.com/en-us/0340ddde-caf4-48ac-8af3-d15dcdade556)



