---
title: Programm zur Verbesserung der Benutzerfreundlichkeit
description: In diesem Artikel erfahren Sie mehr über die Datenschutzeinstellungen in Visual Studio.
ms.date: 05/21/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: PoulChapman
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74ef70228979d1d302a644cda022d086e710b7c7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54921019"
---
# <a name="visual-studio-customer-experience-improvement-program"></a>Programm zur Verbesserung der Benutzerfreundlichkeit von Visual Studio

Das Programm zur Verbesserung der Benutzerfreundlichkeit von Visual Studio (VSCEIP) wurde dafür entwickelt, Microsoft bei der kontinuierlichen Verbesserung von Visual Studio zu unterstützen. Dieses Programm [sammelt Informationen zu Fehlern](../ide/diagnostic-data-collection.md), Computerhardware und der Verwendung von Visual Studio durch die Benutzer, ohne diese bei ihren Aufgaben am Computer zu unterbrechen. Durch die gesammelten Informationen kann Microsoft einfacher ermitteln, welche Features verbessert werden müssen. In diesem Dokument wird erläutert, wie VSCEIP aktiviert oder deaktiviert werden kann.

[!INCLUDE [gdpr-hybrid-note](../misc/includes/gdpr-hybrid-note.md)]

## <a name="opt-in-or-out"></a>Aktivierung oder Deaktivierung

VSCEIP ist standardmäßig aktiviert. Sie können es deaktivieren oder erneut aktivieren, indem Sie folgende Anweisungen befolgen:

1. Starten Sie Visual Studio.

1. Zeigen Sie im **Hilfemenü** auf **Feedback senden**, und wählen Sie dann **Einstellungen** aus.

   Das Dialogfeld **Programm zur Verbesserung der Benutzerfreundlichkeit von Visual Studio** wird geöffnet.

1. Wählen Sie zum Deaktivieren das Optionsfeld **Nein, ich möchte nicht teilnehmen** aus, und klicken Sie auf **OK**.
   Wählen Sie zum Aktivieren das Optionsfeld **Ja, ich möchte teilnehmen (empfohlen)** aus, und klicken Sie auf **OK**.

   ![Dialogfeld „Programm zur Verbesserung der Benutzerfreundlichkeit von Visual Studio“](media/experience-improvement-program.png)

### <a name="registry-settings"></a>Registrierungseinstellungen

Wenn Sie die [Buildtools für Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017) installieren, müssen Sie die Registrierung aktualisieren, um VSCEIP zu konfigurieren. Enterprise-Kunden können durch Festlegen einer registrierungsbasierten Richtlinie eine Gruppenrichtlinie erstellen, um VSCEIP zu aktivieren oder zu deaktivieren.

Der entsprechende Registrierungsschlüssel und die entsprechenden Einstellungen lauten wie folgt:

Schlüssel auf einem 64-Bit-Betriebssystem = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\15.0\SQM** Schlüssel auf einem 32-Bit-Betriebssystem = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\15.0\SQM** Schlüssel bei aktivierter Gruppenrichtlinie = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

Eintrag = **OptIn**

Wert = (DWORD)
- **0** = deaktiviert (VSCEIP deaktivieren)
- **1** = aktiviert (VSCEIP aktivieren)

> [!CAUTION]
> Durch eine falsche Bearbeitung der Registrierung kann das System ernsthaft beschädigt werden. Sie sollten alle wichtigen Daten auf dem Computer zuerst sichern, bevor Sie die Registrierung ändern. Sie können auch die Startoption **Letzte als funktionierend bekannte Konfiguration** verwenden, wenn nach dem Übernehmen manueller Änderungen Probleme auftreten.

Weitere Informationen zu den durch VSCEIP gesammelten, verarbeiteten oder übertragenen Informationen finden Sie in der [Datenschutzerklärung von Microsoft](https://privacy.microsoft.com/privacystatement).

## <a name="see-also"></a>Siehe auch

* [Von Visual Studio gesammelte Diagnoseinformationen](diagnostic-data-collection.md)
* [Sprechen Sie mit uns](../ide/talk-to-us.md)
* [Melden eines Problems mit Visual Studio](../ide/how-to-report-a-problem-with-visual-studio-2017.md)
* [Visual Studio Developer Community](https://developercommunity.visualstudio.com/)
* [Datenschutzerklärung von Microsoft](https://privacy.microsoft.com/privacystatement)
