---
title: Sichere Bereitstellung
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio], security
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- ClickOnce deployment [Office development in Visual Studio], security
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 47cecda571a6826c2d7e845945c05d0264971134
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693330"
---
# <a name="secure-deployment"></a>Sichere Bereitstellung
  Wenn Sie eine Office-Projektmappe erstellen, wird dem Entwicklungscomputer automatisch aktualisiert, um den Code in Ihrem Projekt für die Ausführung zu ermöglichen. Jedoch, wenn Sie die Projektmappe bereitstellen, müssen Beweise auf dem eine Entscheidung über die Vertrauenswürdigkeit basieren, indem Sie die Projektmappe mit einem Zertifikat signieren oder die [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] vorgelegt. Weitere Informationen finden Sie unter [Gewähren von Vertrauenswürdigkeit für Office-Projektmappen](../vsto/granting-trust-to-office-solutions.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Für Anpassungen auf Dokumentebene Wenn Sie das Dokument an einen Netzwerkspeicherort bereitstellen müssen Sie auch den Speicherort des Dokuments zur Liste der vertrauenswürdigen Speicherorte im Sicherheitscenter der Office-Anwendung hinzufügen. Weitere Informationen zum Festlegen der Dokumentberechtigungen auf Endbenutzercomputern finden Sie unter [Gewähren von Vertrauenswürdigkeit für Dokumente](../vsto/granting-trust-to-documents.md).  
  
## <a name="prevent-office-solutions-from-running-code"></a>Verhindern Sie, dass Office-Projektmappen Ausführen von code  
 Administratoren können die Registrierung verwenden, um zu verhindern, dass alle Office-Projektmappen, die auf einem Computer ausgeführt. Wenn eine Office-Projektmappe, die Erweiterungen durch verwalteten Code geöffnet wird, die Visual Studio-Tools für Office Runtime überprüft, ob ein Eintrag mit dem Namen `Disabled` unter einer der folgenden Registrierungsschlüssel auf dem Computer vorhanden:  
  
-   **HKEY_CURRENT_USER\Software\Microsoft\VSTO**  
  
-   **HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO**  
  
 Um zu verhindern, dass Office-Projektmappen Ausführen von Code, erstellen Sie eine `Disabled` Eintrag unter einer oder beide der folgenden Registrierungsschlüssel, und geben Sie einen der folgenden Datentypen und Werte für `Disabled`:  
  
-   REG_SZ oder REG_EXPAND_SZ, die auf eine beliebige Zeichenfolge als "0" (null) festgelegt ist.  
  
-   Einen REG_DWORD-Wert, der auf einen anderen Wert als 0 (null) festgelegt ist.  
  
 Zum Aktivieren von Office-Projektmappen, um Code auszuführen, setzen Sie beide die `Disabled` Einträge auf 0 (null), oder löschen Sie die Registrierungseinträge.  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)   
 [Vorbereiten der Computer zum Ausführen oder Hosten von Office-Projektmappen](http://msdn.microsoft.com/en-us/be1b173f-7261-4d74-aa4e-94ccd43db8d8)   
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)  
  
  