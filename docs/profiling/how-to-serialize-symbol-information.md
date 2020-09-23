---
title: Serialisieren von Symbolinformationen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d644960153a8e342f6442f3750420ea68a61b38f
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851592"
---
# <a name="how-to-serialize-symbol-information"></a>Vorgehensweise: Serialisieren von Symbolinformationen
Sie können Symbole serialisieren, die zum Analysieren Ihrer Anwendung erforderlich sind. Die Serialisierung von Symbolen fügt Symbole in die *VSP-Datei* ein. Durch das Einfügen von Symbolinformationen in die *VSP-Datei* können andere Personen einen Leistungsbericht analysieren, ohne Zugriff auf die Originalsymbole zu haben. Wenn Symbole nicht serialisiert werden, müssen die instrumentierte *EXE-* und *PDB-Dateien* zum Analysieren der *VSP-Datei* vorhanden sein.

### <a name="to-automatically-serialize-symbol-information"></a>So serialisieren Sie automatisch Symbolinformationen

1. Klicken Sie im Menü **Extras** auf **Optionen**.

     Das Dialogfeld **Optionen** wird angezeigt.

2. Klicken Sie auf **Leistungstools**.

3. Wählen Sie unter **Allgemeine Einstellungen** **Symbolinformationen automatisch serialisieren** aus.

## <a name="see-also"></a>Siehe auch
- [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)
- [How to: Verweisen auf Windows-Symbolinformationen](../profiling/how-to-reference-windows-symbol-information.md)
- [How to: Speichern von analysierten Berichten](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\))
