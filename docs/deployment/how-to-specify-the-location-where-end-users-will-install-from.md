---
title: 'Vorgehensweise: Angeben des Speicherorts, in dem Endbenutzer von installieren | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying an installation URL
- URLs, specifying an installation URL
- installation, specifying installation an URL
- Installation URL property
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 3161cfb36c09f78911a762347f9c9ec6d125ee39
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Gewusst wie: Angeben des Speicherorts für die Installation durch Endbenutzer
Beim Veröffentlichen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung, der Speicherort, in dem Benutzer zum Herunterladen und Installieren der Anwendung ist nicht unbedingt der Speicherort, in dem Sie zunächst die Anwendung veröffentlichen. Beispielsweise in einigen Organisationen kann ein Entwickler eine Anwendung auf einem Testserver veröffentlichen, und klicken Sie dann die Anwendung auf einem Webserver ein Administrator verschiebt.  
  
 In diesem Fall können Sie die `Installation URL` -Eigenschaft auf den Webserver festzulegen, wo Benutzer werden die Anwendung herunterladen. Dies ist erforderlich, damit das Anwendungsmanifest weiß, wo nach Updates gesucht werden soll.  
  
 Die `Installation URL` Eigenschaft kann festgelegt werden, auf die **veröffentlichen** auf der Seite der **Projekt-Designer**.  
  
 **Hinweis** der `Installation URL` Eigenschaft kann auch festgelegt werden mithilfe der **PublishWizard**. Weitere Informationen finden Sie unter [Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-specify-an-installation-url"></a>Ein Installations-URL an  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  Geben Sie im Installations-URL-Feld den Installationsspeicherort an, die über eine vollqualifizierte URL im Format http://www.microsoft.com/ApplicationName, oder ein UNC-Pfad im Format \\\Server\ApplicationName.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Angeben des Speicherorts, an den Visual Studio die Dateien kopiert](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Gewusst wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)