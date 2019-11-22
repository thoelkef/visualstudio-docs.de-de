---
title: ClickOnce and Authenticode | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- .pfx files
- ClickOnce deployment, Authenticode
- Authenticode, ClickOnce
- ClickOnce deployment, certificates
- ClickOnce deployment, security
ms.assetid: ab5b6712-f32a-4e33-842f-e88ab4818ccf
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 06edf9954134a6110f9285fc744c87c2696b19d5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298266"
---
# <a name="clickonce-and-authenticode"></a>ClickOnce und Authenticode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Authenticode* is a Microsoft technology that uses industry-standard cryptography to sign application code with digital certificates that verify the authenticity of the application's publisher. Durch die Verwendung von Authenticode bei der Bereitstellung einer Anwendung reduziert [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] das Risiko eines trojanischen Pferdes. Ein trojanisches Pferd ist ein Virus oder ein schädliches Programm, das ein böswilliger Drittanbieter als sicheres Programm aus einer bekannten und vertrauenswürdigen Quelle darstellt. Signieren von [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Bereitstellungen mit einem digitalen Zertifikat ist ein optionaler Schritt, um sicherzustellen, dass die Assemblys und Dateien nicht manipuliert wurden.  
  
 In den folgenden Abschnitten sind die verschiedenen Typen von digitalen Zertifikaten beschrieben, die in Authenticode verwendet werden, wie Zertifikate durch Zertifizierungsstellen (CAs) überprüft werden, die Rolle des Zeitstempels in Zertifikaten und die Methoden des verfügbaren Speichers für Zertifikate.  
  
## <a name="authenticode-and-code-signing"></a>Authenticode und Codesignatur  
 Ein *digitales Zertifikat* ist eine Datei, die ein öffentliches/privates kryptografisches Schlüsselpaar enthält sowie Metadaten über den Herausgeber, für den das Zertifikat ausgestellt wurde, und die Agentur, die das Zertifikat ausgestellt hat.  
  
 Es gibt viele verschiedene Arten von Authenticode-Zertifikaten. Jedes ist für unterschiedliche Arten von Signaturen konfiguriert. Für [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Anwendungen benötigen Sie ein Authenticode-Zertifikat, das zum Signieren von Code gültig ist. Wenn Sie versuchen, eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Anwendung mit einem anderen Typ von Zertifikat zu signieren, z.B. einem digitalen Zertifikat für E-Mail, funktioniert dies nicht. Weitere Informationen finden Sie unter [Einführung in die Codesignatur](https://go.microsoft.com/fwlink/?LinkId=179452).  
  
 Sie können ein Zertifikat für Codesignaturen auf eine von drei Arten abrufen:  
  
- Sie erwerben es von einem Zertifikatsanbieter.  
  
- Sie erhalten es von einer Abteilung in Ihrem Unternehmen, die für das Erstellen von digitalen Zertifikaten verantwortlich ist.  
  
- Sie generieren Ihr eigenes Zertifikat mit MakeCert.exe, das im [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]enthalten ist.  
  
### <a name="how-using-certificate-authorities-helps-users"></a>Wie die Verwendung von Zertifizierungsstellen Benutzern hilft  
 A certificate generated using the MakeCert.exe utility is commonly called a *self-cert* or a *test cert*. This kind of certificate works much the same way that a .snk file works in the .NET Framework. Es besteht ausschließlich aus einem kryptografischen öffentlichen/privaten Schlüsselpaar und enthält keine überprüfbaren Informationen zum Herausgeber. Sie können selbst signierte Zertifikate zum Bereitstellen von [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Anwendungen mit hoher Vertrauenswürdigkeit in einem Intranet verwenden. Beim Ausführen dieser Anwendungen auf einem Clientcomputer wird [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] sie jedoch als von einem unbekannten Herausgeber stammend identifizieren. In der Standardeinstellung können [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Applikationen, die mit selbst signierten Zertifikaten signiert und über das Internet bereitgestellt sind, keine vertrauenswürdige Anwendungsbereitstellung nutzen.  
  
 Wenn Sie dagegen ein Zertifikat von einer Zertifizierungsstelle erhalten, zum Beispiel von einem Zertifikatsanbieter oder einer Abteilung in Ihrem Unternehmen, bietet dieses Zertifikat mehr Sicherheit für Ihre Benutzer. Es identifiziert nicht nur den Herausgeber der signierten Software, sondern überprüft dessen Identität durch Abgleich mit den Daten der Zertifizierungsstelle, die es signiert hat. Wenn die Zertifizierungsstelle nicht die Stammzertifizierungsstelle ist, wird Authenticode auch zurück zur Stammzertifizierungsstelle „verketten“, um zu überprüfen, ob die Zertifizierungsstelle zum Ausstellen von Zertifikaten autorisiert ist. Aus Sicherheitsgründen sollten Sie möglichst ein Zertifikat von einer Zertifizierungsstelle verwenden.  
  
 For more information about generating self-certs, see [Makecert.exe (Certificate Creation Tool)](https://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).  
  
### <a name="timestamps"></a>Timestamps  
 Die Zertifikate zum Signieren von [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Applikationen laufen nach einem bestimmten Zeitraum ab, in der Regel zwölf Monate. Um nicht ständig mit neuen Zertifikaten neu signieren zu müssen, unterstützt [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Timestamps (Zeitstempel). Wenn eine Anwendung mit einem Zeitstempel versehen ist, wird ihr Zertifikat auch nach Ablauf der Gültigkeit des Zertifikats akzeptiert, vorausgesetzt, dass der Zeitstempel gültig ist. Dadurch können [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Anwendungen mit abgelaufenen Zertifikaten, aber gültigen Zeitstempeln, heruntergeladen und ausgeführt werden. Außerdem können installierte Programme mit abgelaufenen Zertifikaten weiterhin Updates herunterladen und installieren.  
  
 Um einen Zeitstempel in einen Anwendungsserver einzuschließen, muss ein Timestampserver verfügbar sein. Weitere Informationen zum Auswählen eines Timestampservers finden Sie unter [How to: Sign Application and Deployment Manifests](../ide/how-to-sign-application-and-deployment-manifests.md).  
  
### <a name="updating-expired-certificates"></a>Aktualisieren von abgelaufenen Zertifikaten  
 In früheren Versionen von .NET Framework verursachte das Aktualisieren einer Anwendung, deren Zertifikat abgelaufen war, den Absturz dieser Anwendung. Sie können eine der folgenden Methoden verwenden, um dieses Problem zu lösen:  
  
- Aktualisieren Sie .NET Framework auf Version 2.0 SP1 oder höher auf Windows XP oder Version 3.5 oder höher auf Windows Vista.  
  
- Deinstallieren Sie die Anwendung, und installieren Sie eine neue Version mit einem gültigen Zertifikat.  
  
- Erstellen Sie eine Befehlszeilen-Assembly, die das Zertifikat aktualisiert. Detaillierte Informationen zu diesem Vorgang finden Sie im [Microsoft Support-Artikel 925521](https://go.microsoft.com/fwlink/?LinkId=179454).  
  
### <a name="storing-certificates"></a>Speichern von Zertifikaten  
  
- Sie können Zertifikate als PFX-Datei im Dateisystem speichern oder in einem Schlüsselcontainer speichern. Ein Benutzer auf einer Windows-Domäne kann über mehrere Schlüsselcontainer verfügen. Standardmäßig werden MakeCert.exe Zertifikate in Ihrem persönlichen Schlüsselcontainer gespeichert, es sei denn, Sie geben an, dass sie in einer PFX-Datei gespeichert werden sollen. Mage.exe und MageUI.exe, die [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] Tools zum Erstellen von [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Bereitstellungen, ermöglichen es Ihnen, auf beide Arten gespeicherte Zertifikate zu verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Sicherheit und -Bereitstellung](../deployment/clickonce-security-and-deployment.md)   
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Überblick über die Bereitstellung vertrauenswürdiger Anwendungen](../deployment/trusted-application-deployment-overview.md)   
 [Mage.exe (Tool zum Generieren und Bearbeiten von Manifesten)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)
