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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 40428d36648e159bd8fa90c2680b660b2112ef5f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53827926"
---
# <a name="secure-deployment"></a>Sichere Bereitstellung
  Wenn Sie eine Office-Projektmappe erstellen, wird Ihrem Entwicklungscomputer automatisch aktualisiert, um in Ihrem Projekt zum Ausführen des Codes zu ermöglichen. Wenn Sie Ihre Lösung bereitstellen, Sie müssen jedoch bereitstellen Beweise auf der eine Entscheidung über die Vertrauenswürdigkeit basieren, indem Sie die Projektmappe mit einem Zertifikat signieren oder die [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] vorgelegt. Weitere Informationen finden Sie unter [Gewähren von Vertrauenswürdigkeit für Office-Projektmappen](../vsto/granting-trust-to-office-solutions.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Für Anpassungen auf Dokumentebene Wenn Sie einen Speicherort im Netzwerk, das Dokument bereitstellen müssen Sie auch den Speicherort des Dokuments der Liste der vertrauenswürdigen Speicherorte im Sicherheitscenter der Office-Anwendung hinzufügen. Weitere Informationen zum Festlegen von Dokumentberechtigungen auf Endbenutzercomputern finden Sie unter [Gewähren von Vertrauenswürdigkeit für Dokumente](../vsto/granting-trust-to-documents.md).  
  
## <a name="prevent-office-solutions-from-running-code"></a>Verhindern Sie, dass Office-Projektmappen Ausführen von code  
 Administratoren können die Registrierung verwenden, um zu verhindern, dass alle Office-Projektmappen auf einem Computer ausgeführt. Wenn eine Office-Projektmappe, die Erweiterungen durch verwalteten Code geöffnet wird, die Visual Studio-Tools für Office-Laufzeit überprüft, ob ein Eintrag mit dem Namen `Disabled` unter einer der folgenden Registrierungsschlüssel auf dem Computer vorhanden:  
  
- **HKEY_CURRENT_USER\Software\Microsoft\VSTO**  
  
- **HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO**  
  
  Um zu verhindern, dass Office-Projektmappen Ausführen von Code, erstellen Sie eine `Disabled` Eintrag unter einer oder beide der folgenden Registrierungsschlüssel, und geben Sie einen der folgenden Datentypen und Werte für `Disabled`:  
  
- Einen REG_SZ- oder REG_EXPAND_SZ, die auf eine beliebige Zeichenfolge als "0" (null) festgelegt ist.  
  
- Einen REG_DWORD-Wert, der auf einen anderen Wert als 0 (null) festgelegt ist.  
  
  Um Office-Projektmappen zum Ausführen von Code zu aktivieren, legen Sie beide die `Disabled` Einträge auf 0 (null) oder die Registrierungseinträge zu löschen.  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)   
 [Vorbereiten der Computer zum Ausführen oder hosten Office-Projektmappen](https://msdn.microsoft.com/be1b173f-7261-4d74-aa4e-94ccd43db8d8)   
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)  
