---
title: 'Vorgehensweise: Verweisen auf Windows-Symbolinformationen | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 347b35a1ed47236c0d6e6c187224ee50fd79852c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619887"
---
# <a name="how-to-reference-windows-symbol-information"></a>Vorgehensweise: Verweisen auf Windows-Symbolinformationen
Die Visual Studio-Profilerstellungstools verwenden Symboldateien (*PDB*), um symbolische Namen wie Funktionsnamen in Programmbinärdateien aufzulösen. Sie können diese Schritte befolgen, um automatisch die richtigen *PDB-Dateien* für die Windows-Version auf dem lokalen Computer herunterzuladen und zu aktualisieren.

> [!NOTE]
>  Diese Einstellung wirkt sich nicht auf vorhandene Berichte aus. Nur Berichte, die nach Angabe des Symbolservers erstellt wurden, werden die Symbolinformationen haben.

 Weitere Informationen finden Sie unter [Angeben von Symboldateien (*PDB*) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

### <a name="to-use-the-microsoft-symbol-server"></a>So verwenden Sie den Microsoft-Symbolserver

1.  Erstellen Sie einen Ordner, um die Symboldateiinformationen aufzubewahren, wie z.B. C:\SymbolCache.

2.  Klicken Sie im Menü **Extras** auf **Optionen**.

     Das Dialogfeld **Optionen** wird angezeigt.

3.  Erweitern Sie die Struktur **Debuggen**, und klicken Sie anschließend auf **Symbole**.

4.  Wählen Sie in **Speicherort für Symboldateien (.pdb)** **Microsoft-Symbolserver** aus

5.  Geben Sie in **Symbole vom Symbolserver zwischenspeichern** den Ordnerpfad ein, der in Schritt 1 erstellt wurde. Beispiel:

     **C:\SymbolCache**

     Sie können auch die Schaltfläche mit den Auslassungszeichen (**...**) anklicken und anschließend ein Verzeichnis vom Dialogfeld **Nach Ordner suchen** auswählen.

## <a name="see-also"></a>Siehe auch
- [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)
- [Vorgehensweise: Serialisieren von Symbolinformationen](../profiling/how-to-serialize-symbol-information.md)