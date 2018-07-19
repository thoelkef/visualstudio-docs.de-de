---
title: 'Vorgehensweise: Angeben des Speicherorts, der dem Endbenutzer aus installieren | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6b0731a5e218b6fcd6a13ac00fe19daad86f6b3d
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078084"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Gewusst wie: Angeben des Speicherorts, der dem Endbenutzer aus installieren
Beim Veröffentlichen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung, der Speicherort, in dem Benutzer zum Herunterladen und installieren Sie die Anwendung ist nicht unbedingt der Speicherort, in dem Sie die Anwendung zunächst veröffentlichen. Beispielsweise wird in einigen Organisationen kann ein Entwickler eine Anwendung auf einem Stagingserver veröffentlichen, und klicken Sie dann ein Administrator verschiebt die Anwendung auf einem Webserver.  
  
 In diesem Fall können Sie die `Installation URL` Eigenschaft, um den Webserver anzugeben, in denen Benutzer aufrufen, die die Anwendung herunterzuladen. Dies ist erforderlich, sodass das Anwendungsmanifest, wo Sie nach Updates suchen kann.  
  
 Die `Installation URL` Eigenschaft kann festgelegt werden, auf die **veröffentlichen** auf der Seite die **Projekt-Designer**.  
  
 **Beachten Sie** der `Installation URL` Eigenschaft kann auch festgelegt werden mithilfe der **Veröffentlichungs-Assistenten**. Weitere Informationen finden Sie unter [Vorgehensweise: veröffentlichen eine ClickOnce-Anwendung, die mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-specify-an-installation-url"></a>Ein Installations-URL angeben.  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen-Explorer**im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die **veröffentlichen** Registerkarte.  
  
3.  Geben Sie im Feld Installations-URL den Speicherort der Installation mithilfe einer vollqualifizierten URL im Format *http://www.microsoft.com/ApplicationName*, oder einen UNC-Pfad im Format  *\\\Server\ApplicationName*.  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: angeben, in denen Visual Studio die Dateien kopiert](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Gewusst wie: veröffentlichen eine ClickOnce-Anwendung, die mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)