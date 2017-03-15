---
title: "Gewusst wie: Hinzuf&#252;gen eines vertrauensw&#252;rdigen Herausgebers zu einem Clientcomputer f&#252;r ClickOnce-Anwendungen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce-Bereitstellung, Installieren ohne Rückfrage"
  - "Vertrauenswürdige Anwendungsbereitstellung, Vertrauenswürdige Herausgeber"
ms.assetid: 35fe324c-45a1-4509-b7be-5c18b4b1b4ab
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# Gewusst wie: Hinzuf&#252;gen eines vertrauensw&#252;rdigen Herausgebers zu einem Clientcomputer f&#252;r ClickOnce-Anwendungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit der Bereitstellung einer vertrauenswürdigen Anwendung können Sie Clientcomputer so konfigurieren, dass Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungen mit einer höheren Vertrauensebene ausgeführt werden ohne den Benutzer dazu aufzufordern. Die folgenden Verfahren zeigen, wie das Befehlszeilentool CertMgr.exe verwendet wird, um das Zertifikat des Herausgebers zum Speicher für vertrauenswürdige Herausgeber auf einem Clientcomputer hinzuzufügen.  
  
 Die von Ihnen verwendeten Befehle weichen leicht davon ab, je nachdem ob die Zertifizierungsstelle, die Ihr Zertifikat herausgegeben hat, Teil eines vertrauenswürdigen Stamms eines Clients ist. Wenn ein Windows\-Clientcomputer Teil einer Domäne ist, enthält er in einer Liste Zertifizierungsstellen, die als vertrauenswürdige Stämme gelten. Diese Liste wird normalerweise vom Systemadministrator konfiguriert. Wenn das Zertifikat von einer der vertrauenswürdigen Stämmen oder von einer Zertifizierungsstelle herausgegeben wurde, die mit einer dieser vertrauenswürdigen Stämme verknüpft ist, können Sie das Zertifikat zum vertrauenswürdigen Stammspeicher des Clients hinzufügen. Wenn andererseits das Zertifikat nicht von einem dieser vertrauenswürdigen Stämme ausgestellt wurde, müssen Sie das Zertifikat jeweils dem vertrauenswürdigen Stammspeicher des Clients und dem Speicher des vertrauenswürdigen Herausgebers hinzufügen.  
  
> [!NOTE]
>  Sie müssen Zertifikate auf diese Weise jedem Clientcomputer hinzufügen, auf dem Sie eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung bereitstellen möchten, die erweiterte Berechtigungen erfordert. Sie können die Zertifikate entweder manuell oder über eine Anwendung hinzufügen, die Sie für Ihre Clients bereitstellen. Sie müssen diese Computer nur einmal konfigurieren. Danach können Sie eine beliebige Anzahl von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungen signiert mit demselben Zertifikat bereitstellen.  
  
 Sie können ein Zertifikat auch mithilfe der Klasse <xref:System.Security.Cryptography.X509Certificates.X509Store> programmgesteuert zu einem Speicher hinzufügen.  
  
 Einen Überblick über die Bereitstellung vertrauenswürdiger Anwendungen finden Sie unter [Überblick über die Bereitstellung vertrauenswürdiger Anwendungen](../deployment/trusted-application-deployment-overview.md).  
  
### So fügen Sie ein Zertifikat zum Speicher für vertrauenswürdige Herausgeber unter dem vertrauenswürdigen Stamm hinzu  
  
1.  Abrufen eines digitales Zertifikats von einer Zertifizierungsstelle.  
  
2.  Exportieren Sie das Zertifikat in das Format Base64 X.509 \(.cer\). Weitere Informationen zu den Zertifikatformaten finden Sie unter [Exportieren eines Zertifikats](http://go.microsoft.com/fwlink/?LinkId=164793).  
  
3.  Führen Sie über die Eingabeaufforderung auf Clientcomputern den folgenden Befehl aus:  
  
     **certmgr.exe \-add certificate.cer \-c \-s \-r localMachine TrustedPublisher**  
  
### So fügen Sie ein Zertifikat zum Speicher für vertrauenswürdige Herausgeber unter einem anderen Stamm hinzu  
  
1.  Abrufen eines digitales Zertifikats von einer Zertifizierungsstelle.  
  
2.  Exportieren Sie das Zertifikat in das Format Base64 X.509 \(.cer\). Weitere Informationen zu den Zertifikatformaten finden Sie unter [Exportieren eines Zertifikats](http://go.microsoft.com/fwlink/?LinkId=164793).  
  
3.  Führen Sie über die Eingabeaufforderung auf Clientcomputern den folgenden Befehl aus:  
  
     **certmgr.exe \-add good.cer \-c \-s \-r localMachine Root**  
  
     **certmgr.exe \-add good.cer \-c \-s \-r localMachine TrustedPublisher**  
  
## Siehe auch  
 [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Sichern von ClickOnce\-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Codezugriffssicherheit für ClickOnce\-Anwendungen](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce und Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Überblick über die Bereitstellung vertrauenswürdiger Anwendungen](../deployment/trusted-application-deployment-overview.md)   
 [How to: Enable ClickOnce Security Settings](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Gewusst wie: Festlegen einer Sicherheitszone für eine ClickOnce\-Anwendung](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Gewusst wie: Festlegen benutzerdefinierter Berechtigungen für eine ClickOnce\-Anwendung](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Gewusst wie: Debuggen einer ClickOnce\-Anwendung mit eingeschränkten Berechtigungen](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [How to: Add a Trusted Publisher to a Client Computer for ClickOnce Applications](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [How to: Re\-sign Application and Deployment Manifests](../deployment/how-to-re-sign-application-and-deployment-manifests.md)   
 [How to: Configure the ClickOnce Trust Prompt Behavior](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)