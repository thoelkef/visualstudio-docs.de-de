---
title: "Gew&#228;hren von Vertrauensw&#252;rdigkeit f&#252;r Office-Projektmappen | Microsoft Docs"
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
  - "Sicherheit [Office-Entwicklung in Visual Studio], Vertrauenswürdigkeit"
  - "Aufnahmelisten [Office-Entwicklung in Visual Studio], Informationen zu Aufnahmelisten"
  - "Vertrauenswürdigkeit [Office-Entwicklung in Visual Studio], 2007 Office System"
  - "Gewähren von Vertrauenswürdigkeit [Office-Entwicklung in Visual Studio]"
ms.assetid: 6c33e614-d367-4556-9e76-0f302ad0f929
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# Gew&#228;hren von Vertrauensw&#252;rdigkeit f&#252;r Office-Projektmappen
  Gewähren von Vertrauenswürdigkeit für Office\-Projektmappen versteht man das Ändern der Sicherheitsrichtlinie jedes Zielcomputers, um der Projektmappenassembly, dem Anwendungsmanifest, dem Bereitstellungsmanifest und dem Dokument zu vertrauen.  Vertrauenswürdigkeit kann der Office\-Projektmappe entweder von Ihnen oder vom Endbenutzer gewährt werden.  
  
 Sie können der Office\-Projektmappe volle Vertrauenswürdigkeit gewähren, indem Sie die Anwendungs\- und Bereitstellungsmanifeste signieren.  
  
 Endbenutzer können der Office\-Lösung Vertrauenswürdigkeit gewähren, indem eine Entscheidung über die Vertrauenswürdigkeit in der [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] vertrauenswürdigen Eingabeaufforderung gelten.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="Signing"></a> Der Projektmappe durch das Signieren von Anwendungs\- und Bereitstellungsmanifesten vertrauen  
 Alle Anwendungs\- und Bereitstellungsmanifeste für Office\-Projektmappen müssen mit einem Zertifikat signiert werden, das den Herausgeber identifiziert.  Zertifikate bilden die Grundlage für Entscheidungen über die Vertrauenswürdigkeit.  
  
 Zur Erstellungszeit wird ein temporäres Zertifikat für Sie erstellt und Vertrauenswürdigkeit gewährt, sodass die Projektmappe ausgeführt werden kann, während Sie sie debuggen.  Wenn Sie eine Projektmappe veröffentlichen, die mit einem temporären Zertifikat signiert ist, wird der Endbenutzer aufgefordert, eine Entscheidung über die Vertrauenswürdigkeit zu treffen.  
  
 Wenn Sie die Projektmappe mit einem bekannten und vertrauenswürdigen Zertifikat signieren, wird die Projektmappe automatisch installiert, ohne dass der Endbenutzer eine Entscheidung über die Vertrauenswürdigkeit treffen muss.  Weitere Informationen darüber, wie Sie ein Zertifikat zum Signieren erhalten, finden Sie unter [ClickOnce and Authenticode](../deployment/clickonce-and-authenticode.md).  Nachdem ein Zertifikat eingeholt wurde, muss das Zertifikat explizit als vertrauenswürdig gekennzeichnet werden, indem es zur Liste vertrauenswürdiger Herausgeber hinzugefügt wird.  Weitere Informationen hierzu finden Sie unter [How to: Add a Trusted Publisher to a Client Computer for ClickOnce Applications](../Topic/How%20to:%20Add%20a%20Trusted%20Publisher%20to%20a%20Client%20Computer%20for%20ClickOnce%20Applications.md).  
  
 Signiert ein Entwickler die Projektmappe mit einem temporären Zertifikat, kann ein Administrator die Anpassung mithilfe des Tools zum Generieren und Bearbeiten von Manifesten \(mage.exe\) erneut mit einem bekannten und vertrauenswürdigen Zertifikat signieren. Dieses Tool gehört zu den Microsoft .NET Framework\-Tools.  Weitere Informationen über das Signieren von Projektmappen finden Sie unter [Gewusst wie: Signieren von Office-Projektmappen](../vsto/how-to-sign-office-solutions.md) und unter [Gewusst wie: Signieren von Anwendungs- und Bereitstellungsmanifesten](../Topic/How%20to:%20Sign%20Application%20and%20Deployment%20Manifests.md).  
  
##  <a name="TrustPrompt"></a> Der Projektmappe mithilfe der vertrauenswürdigen ClickOnce\-Eingabeaufforderung vertrauen  
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] fordert den Endbenutzer auf, eine Entscheidung über die Vertrauenswürdigkeit zu treffen, wenn keine unternehmensweite Richtlinie existiert, aufgrund derer das Zertifikat der Projektmappe als vertrauenswürdig eingestuft wird.  Wenn der Endbenutzer der Projektmappe Vertrauenswürdigkeit gewährt, wird ein Eintrag in der Aufnahmeliste erstellt, der eine URL und einen öffentlichen Schlüssel zum Speichern dieser Entscheidung über die Vertrauenswürdigkeit enthält.  Wenn später eine vertrauenswürdige Anpassung ausgeführt wird, wird dem Endbenutzer keine erneute Aufforderung angezeigt.  
  
 Administratoren können die vertrauenswürdige [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]\-Eingabeaufforderung deaktivieren oder so einrichten, dass die Eingabeaufforderung nur für Projektmappen angezeigt wird, die mit einem Authenticode\-Zertifikat signiert sind.  Weitere Informationen zum Ändern dieser Einstellungen für die Zonen MyComputer, LocalIntranet, Internet, TrustedSites und UntrustedSites finden Sie unter [How to: Configure the ClickOnce Trust Prompt Behavior](../Topic/How%20to:%20Configure%20the%20ClickOnce%20Trust%20Prompt%20Behavior.md).  
  
## Siehe auch  
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)   
 [Gewähren von Vertrauenswürdigkeit für Dokumente](../vsto/granting-trust-to-documents.md)   
 [Problembehandlung bei Office-Projektmappensicherheit](../vsto/troubleshooting-office-solution-security.md)   
 [Überlegungen zur Sicherheit von Office-Projektmappen](../vsto/specific-security-considerations-for-office-solutions.md)  
  
  