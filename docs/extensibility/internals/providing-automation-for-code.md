---
title: "Bereitstellen von Automation für Code | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e59f3826cbb2ed83510cd98209b4c83f9278397d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="providing-automation-for-code"></a>Bereitstellen von Automation für Code
Erstellen ein Automatisierungsmodell für Ihren Code ist nicht erforderlich. Das SDK-Umgebung bietet kein Beispiel hierfür. Einblick in Codemodelle, finden Sie unter der <xref:EnvDTE.CodeModel> Objekt.  
  
 Um ein Codemodell zu implementieren, müssen Sie keine Schnittstellen implementieren, die von der internen Datenstruktur bestimmt werden. Die Objekte aus abgeleitet werden die `IDispatch` Klasse.  
  
 Die Objekte, die Sie erweitern, <xref:EnvDTE.CodeModel> und <xref:EnvDTE.FileCodeModel>, stehen über die <xref:EnvDTE.Project> -Objekt, und wie folgt aussehen:  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 Sie können festlegen, ob die implementieren nur die `CodeModel` oder die `FileCodeModel` Schnittstelle im zurückgegebenen Objekt Ihre `Project` und <xref:EnvDTE.ProjectItem> Objekte. Geben Sie keine Funktionen aus dieser Schnittstelle, die für Ihr Projektsystem geeignet ist.  
  
 Wenn Sie Funktionen wie Methoden oder Eigenschaften, hinzufügen möchten, die stehen nicht vom Standard `CodeModel` und `FileCodeModel` Schnittstellen, erstellen Sie eine eigene Schnittstelle, die vom Standard erbt. Achten Sie darauf, dass Sie mit Ihrem Projektsystem zu dokumentieren, und Endbenutzer vertraut sind, um dafür zu suchen. Sie geben die standard-Schnittstelle zurück, aber der Benutzer kann das Aufrufen der `QueryInterface` -Methode oder Cast auf Ihre Schnittstelle, wenn es bekannt ist, vorhanden sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über das Automatisierungsmodell](../../extensibility/internals/automation-model-overview.md)