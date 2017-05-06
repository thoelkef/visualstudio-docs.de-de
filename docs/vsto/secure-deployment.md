---
title: "Sichere Bereitstellung"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ClickOnce-Bereitstellung [Office-Entwicklung in Visual Studio], Sicherheit"
  - "Bereitstellen von Anwendungen [Office-Entwicklung in Visual Studio], Sicherheit"
  - "Office-Anwendungen [Office-Entwicklung in Visual Studio], Sicherheit"
  - "Office-Entwicklung in Visual Studio, Sicherheit"
ms.assetid: c5ba86b1-e87f-4508-8c5a-1295681a9590
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Sichere Bereitstellung
  Beim Erstellen einer Office\-Lösung wird der Entwicklungscomputer automatisch aktualisiert, damit der Projektcode ausgeführt werden kann.  Wird die Lösung bereitgestellt, müssen Beweise vorgelegt werden, anhand derer eine Entscheidung bezüglich der Vertrauenswürdigkeit getroffen werden kann. Dabei wird die Lösung mit einem Zertifikat signiert oder der Schlüssel für die vertrauenswürdige [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]\-Eingabeaufforderung verwendet.  Weitere Informationen finden Sie unter [Gewähren von Vertrauenswürdigkeit für Office-Projektmappen](../vsto/granting-trust-to-office-solutions.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Für Anpassungen auf Dokumentebene muss im Falle der Bereitstellung des Dokuments für einen Netzwerkspeicherort auch der Speicherort des Dokuments der Liste der vertrauenswürdigen Speicherorte hinzugefügt werden \(die Liste befindet sich im Sicherheitscenter der Office\-Anwendung\).  Weitere Informationen zum Festlegen der Dokumentberechtigungen auf Endbenutzercomputern finden Sie unter [Gewähren von Vertrauenswürdigkeit für Dokumente](../vsto/granting-trust-to-documents.md).  
  
## Verhindern der Ausführung von Code in Office\-Projektmappen  
 Administratoren können mithilfe der Registrierung verhindern, dass alle Office\-Projektmappen auf einem Computer ausgeführt werden.  Wenn eine Office\-Projektmappe, die Erweiterungen durch verwalteten Code auf, geöffnet ist, die Visual Studio Tools für Office\-Ablaufüberprüfungen, ob ein Eintrag mit dem Namen `Disabled` unter einem der folgenden Registrierungsschlüssel auf dem Computer vorhanden ist:  
  
-   `HKEY_CURRENT_USER\Software\Microsoft\VSTO`  
  
-   `HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO`  
  
 Um Office\-Projektmappen am Ausführen von Code zu hindern, erstellen Sie unter einem der Registrierungsschlüssel oder unter beiden Schlüsseln einen `Disabled`\-Eintrag, und geben Sie für `Disabled` einen der folgenden Datentypen und Werte an:  
  
-   REG\_SZ oder REG\_EXPAND\_SZ, wobei als Zeichenfolge ein anderer Wert als "0" \(Null\) angegeben ist.  
  
-   REG\_DWORD mit einem anderen Wert als 0 \(Null\).  
  
 Um die Codeausführung für Office\-Projektmappen zu aktivieren, legen Sie beide `Disabled`\-Einträge auf 0 \(Null\) fest, oder löschen Sie die Registrierungseinträge.  
  
## Siehe auch  
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)   
 [Vorbereiten von Computern für das Ausführen oder Hosten von Office\-Lösungen](http://msdn.microsoft.com/de-de/be1b173f-7261-4d74-aa4e-94ccd43db8d8)   
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)  
  
  