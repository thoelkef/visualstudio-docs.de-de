---
title: Synchronisieren von Typ und den Dateinamen - Umgestaltung (c#) | Microsoft Docs
ms.custom: 
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48172dd7-24a5-4884-8a73-f92497ad6a0d
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs: CSharp
ms.openlocfilehash: ee37983575aa82abb764d57006cdabd094ea6497
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-in-c"></a>Synchronisieren eines Typs in einen Dateinamen oder einen Dateinamen in einen Typ in c# #

<!-- VERSIONLESS -->
**Diese Funktion ist in Visual Studio 2017 und höher verfügbar.  Für diese Umgestaltung sind .NET Standardprojekten darüber hinaus noch nicht unterstützt.**

**Was:** können Sie einen Typ den Dateinamen entsprechend umbenennen oder benennen Sie einen Dateinamen entsprechend den Typ, es enthält.

**Wann:** umbenannt haben, eine Datei oder einen Typ und noch nicht noch die entsprechende Datei oder der Typ entsprechend aktualisiert. 

**Grund:** überführen einen Typ in eine Datei mit einem anderen Namen oder umgekehrt, es schwer zu finden, wonach Sie suchen.  Durch das Umbenennen der Typ oder der Dateiname, wird Code besser lesbar und einfacher zu navigieren.

**Vorgehensweise:**

1. Markieren Sie, oder platzieren Sie den Textcursor innerhalb der Name des Typs zu synchronisieren:

   ![Hervorgehobene code](media/synctype_highlight.png)

1. Als Nächstes führen Sie eine der folgenden:
   * **Tastatur**
     * Drücken Sie **STRG +.** Trigger die **Schnellaktionen und Refactorings** , und wählen Sie im Menü **Datei umbenennen *TypeName*cs** aus Popup-Fenster "Vorschau", in denen *TypeName* ist der Name des Typs, die Sie ausgewählt haben.
     * Drücken Sie **STRG +.** Trigger die **Schnellaktionen und Refactorings** Menü **umbenennen zum Typ _Filename_**  aus Popup-Fenster "Vorschau", in denen *Filename* ist der Name der aktuellen Datei.
   * **Maus**
     * Mit der rechten Maustaste in des Codes, wählen Sie die **Schnellaktionen und Refactorings** , und wählen **Datei umbenennen *TypeName*cs** aus Popup-Fenster "Vorschau", in dem *Typname* ist der Name des Typs, die Sie ausgewählt haben.
     * Mit der rechten Maustaste in des Codes, wählen Sie die **Schnellaktionen und Refactorings** , und wählen **umbenennen zum Typ _Filename_**  aus Popup-Fenster "Vorschau", in dem  *FileName* ist der Name der aktuellen Datei.

   Der Typ oder die Datei wird sofort umbenannt werden.  Im nachfolgenden Beispiel wird die Datei **MyClass.cs** wurde umbenannt in **MyNewClass.cs** mit dem Namen des Typs übereinstimmen.

   ![Inline-Ergebnis](media/synctype_result.png)

## <a name="see-also"></a>Siehe auch  
[Refactoring (C#)](../refactoring-csharp.md)
