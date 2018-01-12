---
title: "Gewähren von Vertrauenswürdigkeit für Office-Projektmappen | Microsoft Docs"
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
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 41ecf50a7306025913f228500036d133918dd31b
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="granting-trust-to-office-solutions"></a>Gewähren von Vertrauenswürdigkeit für Office-Projektmappen
  Gewähren von Vertrauenswürdigkeit für Office-Projektmappen bedeutet das Ändern der Sicherheitsrichtlinie des jeder Zielcomputer die Projektmappenassembly, Anwendungsmanifest Bereitstellungsmanifest und Dokument zu vertrauen. Office-Projektmappe können Sie oder der Benutzer Vertrauenswürdigkeit gewährt werden.  
  
 Sie können die volle Vertrauenswürdigkeit für Office-Projektmappe erteilen, indem Sie die Anwendungs- und Bereitstellungsmanifeste zu signieren.  
  
 Endbenutzer können der Office-Projektmappe Vertrauenswürdigkeit zu erteilen, indem Sie eine Entscheidung hinsichtlich der Vertrauenswürdigkeit in der [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] vertrauensaufforderung.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="Signing"></a>Vertrauen die Projektmappe durch das Signieren der Anwendung und die Bereitstellung Manifeste  
 Alle-Anwendungsmanifest und-Bereitstellungsmanifest für Office-Projektmappen mit einem Zertifikat signiert werden müssen, die den Herausgeber identifiziert. Zertifikate ermöglichen eine Grundlage zum treffen von Entscheidungen zur Vertrauenswürdigkeit.  
  
 Ein temporäres Zertifikat für Sie erstellt und zur Buildzeit Vertrauenswürdigkeit gewährt werden, damit die Projektmappe ausgeführt werden kann, während Sie debuggen. Wenn Sie eine Projektmappe, die zusammen ein temporäres Zertifikat signiert ist veröffentlichen, werden der Endbenutzer aufgefordert werden, um eine Vertrauensstellung Entscheidung zu treffen.  
  
 Wenn Sie die Projektmappe mit einem bekannten und vertrauenswürdigen Zertifikat signieren, wird die Projektmappe automatisch installiert werden, ohne den Endbenutzer, um eine Vertrauensstellung Entscheidung zu treffen. Weitere Informationen zum Abrufen eines Zertifikats zum Signieren finden Sie unter [ClickOnce und Authenticode](/visualstudio/deployment/clickonce-and-authenticode). Nachdem Sie ein Zertifikat erworben haben, ist, muss das Zertifikat explizit vertrauenswürdig sein, indem sie Sie der Liste der vertrauenswürdigen Herausgeber hinzufügen. Weitere Informationen finden Sie unter [wie: Hinzufügen von einem vertrauenswürdigen Herausgeber auf einem Clientcomputer für ClickOnce-Anwendungen](/visualstudio/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications).  
  
 Wenn ein Entwickler die Projektmappe mit einem temporären Zertifikat signiert werden, kann ein Administrator erneut die Anpassung mit einem bekannten und vertrauenswürdigen Zertifikat mit dem Manifest Tool zum Generieren und bearbeiten (mage.exe), dies ist eine von Microsoft .NET Framework-Tools melden. Weitere Informationen zum Signieren von Lösungen finden Sie unter [wie: Signieren von Office-Projektmappen](../vsto/how-to-sign-office-solutions.md) und [wie: Signieren von Anwendungs- und Bereitstellungsmanifeste](/visualstudio/ide/how-to-sign-application-and-deployment-manifests).  
  
##  <a name="TrustPrompt"></a>Gewähren von Vertrauenswürdigkeit der Projektmappe mithilfe von der ClickOnce-Vertrauensaufforderung  
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]fordert der Endbenutzer die Vertrauensstellung Entscheidung zu treffen, wenn keine organisationsweite Richtlinie, die das Zertifikat der Projektmappe als vertrauenswürdig eingestuft. Wenn der Benutzer der Projektmappe Vertrauenswürdigkeit gewährt wird, wird ein Eintrag der Aufnahmeliste erstellt, die eine URL und einen öffentlichen Schlüssel zum Speichern dieser Entscheidung über die Vertrauenswürdigkeit enthält. Wenn eine vertrauenswürdige Anpassung später ausgeführt wird, wird der Endbenutzer nicht erneut aufgefordert werden.  
  
 Administratoren können Deaktivieren der [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] vertrauenswürdige Eingabeaufforderung oder erfordern, dass die Meldung nur für Projektmappen auf auftreten, die mit einem Authenticode-Zertifikat signiert sind. Weitere Informationen zum Ändern der Einstellungen für die Zonen MyComputer, LocalIntranet, Internet, TrustedSites und UntrustedSites finden Sie unter [Vorgehensweise: Konfigurieren der ClickOnce-vertrauen Verhalten der Authentifizierungeingabeaufforderung](/visualstudio/deployment/how-to-configure-the-clickonce-trust-prompt-behavior).  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)   
 [Gewähren von Vertrauenswürdigkeit für Dokumente](../vsto/granting-trust-to-documents.md)   
 [Problembehandlung bei Office-Projektmappensicherheit](../vsto/troubleshooting-office-solution-security.md)   
 [Überlegungen zur Sicherheit von Office-Projektmappen](../vsto/specific-security-considerations-for-office-solutions.md)  
  
  