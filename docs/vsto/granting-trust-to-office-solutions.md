---
title: Gewähren von Vertrauen für Office-Projektmappen
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
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 50eeba9769bcfb54a38cd458e85988d2a679b687
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648725"
---
# <a name="grant-trust-to-office-solutions"></a>Gewähren von Vertrauen für Office-Projektmappen
  Gewähren von Vertrauen für Office-Projektmappen bedeutet, dass Ändern der Sicherheitsrichtlinie von jedem Zielcomputer, die Projektmappenassembly, Anwendungsmanifest, Bereitstellungsmanifest und Dokument zu vertrauen. Office-Projektmappe können Sie oder der Endbenutzer Vertrauenswürdigkeit gewährt werden.  
  
 Sie können die Office-Projektmappen volles Vertrauen gewähren, indem Sie die Anwendungs- und Bereitstellungsmanifeste zu signieren.  
  
 Endbenutzer können der Office-Projektmappe Vertrauenswürdigkeit gewähren, indem Sie eine Entscheidung hinsichtlich der Vertrauenswürdigkeit in der [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] vertrauenswürdige Eingabeaufforderung.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="Signing"></a> Vertrauen Sie der Projektmappe, indem die Anwendungs- und Bereitstellungsmanifeste zu signieren  
 Alle-Anwendungsmanifest und-Bereitstellungsmanifest für Office-Lösungen mit einem Zertifikat signiert werden müssen, die den Herausgeber identifiziert. Zertifikate ermöglichen eine Basis zum treffen von Entscheidungen zur Vertrauenswürdigkeit.  
  
 Ein temporäres Zertifikat für Sie erstellt und zum Zeitpunkt der Erstellung Vertrauenswürdigkeit gewährt werden, damit die Projektmappe beim Debuggen ausgeführt wird. Wenn Sie eine Lösung, die mit der ein temporäres Zertifikat signiert ist veröffentlichen, werden die Endbenutzer aufgefordert, eine Vertrauensstellung Entscheidung zu treffen.  
  
 Wenn Sie die Projektmappe mit einem bekannten und vertrauenswürdigen Zertifikat anmelden, wird die Projektmappe automatisch installiert werden, ohne dem Benutzer eine Entscheidung hinsichtlich der Vertrauenswürdigkeit. Weitere Informationen zur Vorgehensweise zum Abrufen eines Zertifikats zum Signieren finden Sie unter [ClickOnce und Authenticode](/visualstudio/deployment/clickonce-and-authenticode). Nachdem Sie ein Zertifikat abgerufen wird, muss das Zertifikat explizit vertrauenswürdig sein, indem sie Sie der Liste vertrauenswürdiger Herausgeber hinzufügen. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen eines vertrauenswürdigen Herausgebers auf einen Clientcomputer für ClickOnce-Anwendungen](/visualstudio/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications).  
  
 Wenn ein Entwickler die Lösung mit einem temporären Zertifikat signiert, ein Administrator kann erneut signieren die Anpassung mit einem bekannten und vertrauenswürdigen Zertifikat mit dem Manifest Generation and Editing Tool (*mage.exe*), einer der der Microsoft .NET Framework-Tools. Weitere Informationen zum Signieren von Lösungen finden Sie unter [Vorgehensweise: Signieren von Office-Projektmappen](../vsto/how-to-sign-office-solutions.md) und [Vorgehensweise: Signieren von Anwendungs- und Bereitstellungsmanifeste](/visualstudio/ide/how-to-sign-application-and-deployment-manifests).  
  
##  <a name="TrustPrompt"></a>Vertrauen Sie der Projektmappe mithilfe der ClickOnce-vertrauensaufforderung  
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] fordert den Endbenutzer auf die Vertrauensstellung Entscheidung zu treffen, wenn keine organisationsweite Richtlinie, die das Zertifikat der Projektmappe als vertrauenswürdig eingestuft. Wenn der Benutzer der Projektmappe Vertrauenswürdigkeit gewährt, wird ein Eintrag der Aufnahmeliste erstellt, die eine URL und einen öffentlichen Schlüssel zum Speichern von dieser Entscheidung über die Vertrauenswürdigkeit enthält. Wenn eine vertrauenswürdige Anpassung später ausgeführt wird, wird der Endbenutzer nicht erneut aufgefordert werden.  
  
 Administratoren können Deaktivieren der [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] vertrauenswürdige Eingabeaufforderung oder erfordern, dass die Aufforderung nur für Projektmappen ausgeführt werden, die mit einem Authenticode-Zertifikat signiert sind. Weitere Informationen zum Ändern dieser Einstellungen für die Zonen "Arbeitsplatz" "," LocalIntranet "," Internet "," TrustedSites, und "UntrustedSites finden Sie unter [Vorgehensweise: Konfigurieren des Verhaltens der ClickOnce Vertrauenswürdigkeit auffordern](/visualstudio/deployment/how-to-configure-the-clickonce-trust-prompt-behavior).  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)   
 [Gewähren von Vertrauen für Dokumente](../vsto/granting-trust-to-documents.md)   
 [Problembehandlung bei Office-projektmappensicherheit](../vsto/troubleshooting-office-solution-security.md)   
 [Besondere sicherheitsüberlegungen für Office-Projektmappen](../vsto/specific-security-considerations-for-office-solutions.md)  
  
  