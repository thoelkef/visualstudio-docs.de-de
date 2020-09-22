---
title: Sichere Bereitstellung
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio], security
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- ClickOnce deployment [Office development in Visual Studio], security
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c838eddea5b3118c28fb33411a8c58a19d7b4a2d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810953"
---
# <a name="secure-deployment"></a>Sichere Bereitstellung
  Wenn Sie eine Office-Projekt Mappe erstellen, wird der Entwicklungs Computer automatisch aktualisiert, damit der Code in Ihrem Projekt ausgeführt werden kann. Wenn Sie die Lösung bereitstellen, müssen Sie jedoch einen Beweis dafür bereitstellen, welche Grundlage eine Vertrauensstellungs Entscheidung bilden soll, indem Sie die Lösung mit einem Zertifikat signieren oder die Eingabeaufforderung für die Vertrauenswürdigkeit verwenden [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Weitere Informationen finden Sie unter [Gewähren von Vertrauenswürdigkeit für Office](../vsto/granting-trust-to-office-solutions.md)-Projektmappen.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Wenn Sie das Dokument für Anpassungen auf Dokument Ebene an einem Netzwerk Speicherort bereitstellen, müssen Sie auch den Speicherort des Dokuments der Liste der vertrauenswürdigen Speicherorte im Trust Center der Office-Anwendung hinzufügen. Weitere Informationen zum Festlegen von Dokument Berechtigungen auf Endbenutzer Computern finden Sie unter Gewähren von [Vertrauenswürdigkeit für Dokumente](../vsto/granting-trust-to-documents.md).

## <a name="prevent-office-solutions-from-running-code"></a>Verhindern, dass Office-Projektmappen Code ausführen
 Administratoren können die Registrierung verwenden, um zu verhindern, dass alle Office-Projektmappen auf einem Computer ausgeführt werden. Wenn eine Office-Projekt Mappe mit Erweiterungen für verwalteten Code geöffnet wird, überprüft der Visual Studio-Tools für Office-Laufzeit, ob ein Eintrag mit dem Namen `Disabled` unter einem der folgenden Registrierungsschlüssel auf dem Computer vorhanden ist:

- **HKEY_CURRENT_USER \software\microsoft\vsto**

- **HKEY_LOCAL_MACHINE \software\microsoft\vsto**

  Um zu verhindern, dass Office-Projektmappen Code ausführen, erstellen Sie einen `Disabled` Eintrag unter einem oder beiden dieser Registrierungsschlüssel, und geben Sie einen der folgenden Datentypen und Werte für an `Disabled` :

- Ein REG_SZ oder REG_EXPAND_SZ, der auf eine beliebige Zeichenfolge außer "0" (null) festgelegt ist.

- Ein-REG_DWORD, der auf einen anderen Wert als 0 (null) festgelegt ist.

  Um Office-Projektmappen das Ausführen von Code zu ermöglichen, legen Sie beide `Disabled` Einträge auf 0 (null) fest, oder löschen Sie die Registrierungseinträge.

## <a name="see-also"></a>Siehe auch
- [Bereitstellen einer Office-Projekt Mappe](../vsto/deploying-an-office-solution.md)
- [Vorbereiten von Computern zum Ausführen oder Hosten von Office-Lösungen](/previous-versions/bb772092(v=vs.110))
- [Sichere Office-Lösungen](../vsto/securing-office-solutions.md)