---
title: 'Vorgehensweise: Angeben der zu startenden Binärdatei | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c569b9e285e4865b8ef637443acdf6026b0fec9c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868468"
---
# <a name="how-to-specify-the-binary-to-start"></a>Vorgehensweise: Angeben der zu startenden Binärdatei

Um ein Profil für Binärdateien zu erstellen, wie z.B. DLLs, müssen Sie Informationen im Dialogfeld  **\<Ziel> Eigenschaftenseiten** eingeben. Diese Informationen geben an, wo das DLL-Projekt die aufrufende Anwendung finden kann.

1. Klicken Sie im **Leistungs-Explorer** mit der rechten Maustaste auf die Zielbinärdatei und anschließend auf **Eigenschaften**.

2. Klicken Sie im Dialogfeld **Eigenschaftenseiten** auf die **Start**-Eigenschaften.

3. Wählen Sie das Kontrollkästchen **Projekteigenschaften überschreiben** aus.

4. Geben Sie m Textfeld **Zu startende ausführbare Datei** den Dateispeicherort an.

5. Geben Sie im **Argumente**-Textfeld Argumente an, die zum Starten der Anwendung erforderlich sind.

6. Geben Sie im **Arbeitsverzeichnis** den Speicherort für das Verzeichnis an.

7. Klicken Sie auf **OK**.

## <a name="see-also"></a>Siehe auch

[Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)