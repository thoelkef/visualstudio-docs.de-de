---
title: Bereitstellen von Automation für Code | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9f9dbb7a8ddad39f01f5b29443168eebe12a2da8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
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