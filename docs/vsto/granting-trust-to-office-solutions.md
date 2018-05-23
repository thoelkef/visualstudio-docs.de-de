---
title: Gewähren von Vertrauenswürdigkeit für Office-Projektmappen
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: cfce58ca765e7e3710ecb55a1c84c09f0ee14f52
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2018
---
# <a name="grant-trust-to-office-solutions"></a>Gewähren von Vertrauenswürdigkeit für Office-Projektmappen
  Gewähren von Vertrauen für Office-Projektmappen bedeutet Ändern der Sicherheitsrichtlinie von jedem Zielcomputer, die Projektmappenassembly, Anwendungsmanifest Bereitstellungsmanifest und Dokument zu vertrauen. Office-Projektmappe können Sie oder der Benutzer Vertrauenswürdigkeit gewährt werden.  
  
 Sie können die volle Vertrauenswürdigkeit für Office-Projektmappe erteilen, indem Sie die Anwendungs- und Bereitstellungsmanifeste zu signieren.  
  
 Endbenutzer können der Office-Projektmappe Vertrauenswürdigkeit zu erteilen, indem Sie eine Entscheidung hinsichtlich der Vertrauenswürdigkeit in der [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] vertrauensaufforderung.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="Signing"></a> Vertrauen Sie die Projektmappe durch das Signieren der Anwendungs- und Bereitstellungsmanifesten  
 Alle-Anwendungsmanifest und-Bereitstellungsmanifest für Office-Projektmappen mit einem Zertifikat signiert werden müssen, die den Herausgeber identifiziert. Zertifikate ermöglichen eine Grundlage zum treffen von Entscheidungen zur Vertrauenswürdigkeit.  
  
 Ein temporäres Zertifikat für Sie erstellt und zur Buildzeit Vertrauenswürdigkeit gewährt werden, damit die Projektmappe ausgeführt werden kann, während Sie debuggen. Wenn Sie eine Projektmappe, die zusammen ein temporäres Zertifikat signiert ist veröffentlichen, werden der Endbenutzer aufgefordert werden, um eine Vertrauensstellung Entscheidung zu treffen.  
  
 Wenn Sie die Projektmappe mit einem bekannten und vertrauenswürdigen Zertifikat signieren, wird die Projektmappe automatisch installiert werden, ohne den Endbenutzer, um eine Vertrauensstellung Entscheidung zu treffen. Weitere Informationen zum Abrufen eines Zertifikats zum Signieren finden Sie unter [ClickOnce und Authenticode](/visualstudio/deployment/clickonce-and-authenticode). Nachdem Sie ein Zertifikat erworben haben, ist, muss das Zertifikat explizit vertrauenswürdig sein, indem sie Sie der Liste der vertrauenswürdigen Herausgeber hinzufügen. Weitere Informationen finden Sie unter [wie: Hinzufügen eines vertrauenswürdigen Herausgebers auf einen Clientcomputer für ClickOnce-Anwendungen](/visualstudio/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications).  
  
 Wenn ein Entwickler die Projektmappe mit einem temporären Zertifikat signiert, ein Administrator kann erneut anmelden, die Anpassung mit einem bekannten und vertrauenswürdigen Zertifikat mit dem Manifest Tool zum Generieren und bearbeiten (*mage.exe*), also eine von der Microsoft .NET Framework-Tools. Weitere Informationen zum Signieren von Lösungen finden Sie unter [wie: Signieren von Office-Projektmappen](../vsto/how-to-sign-office-solutions.md) und [wie: Signieren von Anwendungs- und Bereitstellungsmanifeste](/visualstudio/ide/how-to-sign-application-and-deployment-manifests).  
  
##  <a name="TrustPrompt"></a>Vertrauen Sie der Projektmappe mithilfe von ClickOnce-vertrauensaufforderung  
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] fordert der Endbenutzer die Vertrauensstellung Entscheidung zu treffen, wenn keine organisationsweite Richtlinie, die das Zertifikat der Projektmappe als vertrauenswürdig eingestuft. Wenn der Benutzer der Projektmappe Vertrauenswürdigkeit gewährt wird, wird ein Eintrag der Aufnahmeliste erstellt, die eine URL und einen öffentlichen Schlüssel zum Speichern dieser Entscheidung über die Vertrauenswürdigkeit enthält. Wenn eine vertrauenswürdige Anpassung später ausgeführt wird, wird der Endbenutzer nicht erneut aufgefordert werden.  
  
 Administratoren können Deaktivieren der [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] vertrauenswürdige Eingabeaufforderung oder erfordern, dass die Meldung nur für Projektmappen auf auftreten, die mit einem Authenticode-Zertifikat signiert sind. Weitere Informationen zum Ändern der Einstellungen für die Zonen MyComputer, LocalIntranet, Internet, TrustedSites und UntrustedSites finden Sie unter [Vorgehensweise: Konfigurieren Sie das Verhalten der authentifizierungeingabeaufforderung Vertrauensstellung ClickOnce](/visualstudio/deployment/how-to-configure-the-clickonce-trust-prompt-behavior).  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)   
 [Gewähren von Vertrauenswürdigkeit für Dokumente](../vsto/granting-trust-to-documents.md)   
 [Problembehandlung bei Office-projektmappensicherheit](../vsto/troubleshooting-office-solution-security.md)   
 [Besondere sicherheitsüberlegungen für Office-Projektmappen](../vsto/specific-security-considerations-for-office-solutions.md)  
  
  