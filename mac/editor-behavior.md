---
title: Editor-Verhalten | Microsoft-Dokumentation
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 81EE4460-26EB-4BB0-9297-932E1F88E4B8
ms.openlocfilehash: 3515dfbf3a7cf8c23178aa9df243638f955593e9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="editor-behavior"></a>Editor-Verhalten

Editor-Verhalten kann festgelegt werden, um das Formatieren von Code beim Schreiben zu ermöglichen. Diese Aktionen können unter **Visual Studio > Einstellungen > Text-Editor > Verhalten** festgelegt werden. Einige der häufiger verwendeten Funktionen werden unten beschrieben:

![Optionen Editor-Verhalten](media/source-editor-image9.png)

*  Entsprechende schließende geschweifte Klammern können Code automatisch hinzugefügt werden, wenn Sie neue Klassen, Methoden und Eigenschaften erstellen. Wenn diese Option aktiviert ist, wird durch das Eingeben von `{` automatisch `}` hinzugefügt.
* Die dynamische Codeformatierung wird durch das Drücken von Zeichen wie z.B. Semikolon oder geschweiften Klammern ausgelöst, wodurch die festgelegten Formatierungseinstellungen emuliert werden.
* Sie können die Datei auch formatieren, wenn Sie sie speichern, wodurch Code wie gewünscht geschrieben werden kann, und die Codeformatierung der IDE entsprechend den vorhandenen Einstellungen überlassen.
* Der Einzug kann auf „Keiner“, „Auto“ und „Intelligent“ festgelegt werden. Dadurch passiert Folgendes:
 * Keiner: legt die Einfügemarke auf den Anfang der nächsten Zeile fest
 * Auto: legt die Einfügemarke auf die gleiche Spalte in der nächsten Zeile fest
 * Intelligent: zieht in der folgenden Zeile basierend auf dem Code ein
* Verhalten zur Wörtertrennung unterscheidet sich je nach Betriebssystem. Aus Navigationsgründen muss der Text-Editor wissen, wo Wörter beginnen und enden. Die Formatierung kann auf Unix oder Windows festgelegt werden.

Darüber hinaus können Sie Formatierungsregeln für XML, CSS, HTML und JSON festlegen.