---
title: Sichere Bereitstellung | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio], security
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- ClickOnce deployment [Office development in Visual Studio], security
ms.assetid: c5ba86b1-e87f-4508-8c5a-1295681a9590
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c77d5fb404be8dda323720c1e0c1ab2c1887c88f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="secure-deployment"></a>Sichere Bereitstellung
  Wenn Sie eine Office-Projektmappe erstellen, wird dem Entwicklungscomputer automatisch aktualisiert, um den Code in Ihrem Projekt für die Ausführung zu ermöglichen. Jedoch, wenn Sie die Projektmappe bereitstellen, müssen Beweise auf dem eine Entscheidung über die Vertrauenswürdigkeit basieren, indem Sie die Projektmappe mit einem Zertifikat signieren oder die [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] vorgelegt. Weitere Informationen finden Sie unter [Gewähren von Vertrauenswürdigkeit für Office-Projektmappen](../vsto/granting-trust-to-office-solutions.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Für Anpassungen auf Dokumentebene Wenn Sie das Dokument an einen Netzwerkspeicherort bereitstellen müssen Sie auch den Speicherort des Dokuments zur Liste der vertrauenswürdigen Speicherorte im Sicherheitscenter der Office-Anwendung hinzufügen. Weitere Informationen zum Festlegen der Dokumentberechtigungen auf Endbenutzercomputern finden Sie unter [Gewähren von Vertrauenswürdigkeit für Dokumente](../vsto/granting-trust-to-documents.md).  
  
## <a name="preventing-office-solutions-from-running-code"></a>Verhindert, dass Office-Projektmappen Ausführen von Code  
 Administratoren können die Registrierung verwenden, um zu verhindern, dass alle Office-Projektmappen, die auf einem Computer ausgeführt. Wenn eine Office-Projektmappe, die Erweiterungen durch verwalteten Code geöffnet wird, die Visual Studio-Tools für Office Runtime überprüft, ob ein Eintrag mit dem Namen `Disabled` unter einer der folgenden Registrierungsschlüssel auf dem Computer vorhanden:  
  
-   `HKEY_CURRENT_USER\Software\Microsoft\VSTO`  
  
-   `HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO`  
  
 Um zu verhindern, dass Office-Projektmappen Ausführen von Code, erstellen Sie eine `Disabled` Eintrag unter einer oder beide der folgenden Registrierungsschlüssel, und geben Sie einen der folgenden Datentypen und Werte für `Disabled`:  
  
-   REG_SZ oder REG_EXPAND_SZ, die auf eine beliebige Zeichenfolge als "0" (null) festgelegt ist.  
  
-   Einen REG_DWORD-Wert, der auf einen anderen Wert als 0 (null) festgelegt ist.  
  
 Zum Aktivieren von Office-Projektmappen, um Code auszuführen, setzen Sie beide die `Disabled` Einträge auf 0 (null), oder löschen Sie die Registrierungseinträge.  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen einer Office-Lösung](../vsto/deploying-an-office-solution.md)   
 [Vorbereiten von Computern zum Ausführen oder Hosten von Office-Projektmappen](http://msdn.microsoft.com/en-us/be1b173f-7261-4d74-aa4e-94ccd43db8d8)   
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)  
  
  