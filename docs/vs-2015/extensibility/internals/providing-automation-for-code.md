---
title: Bereitstellen von Automatisierung für Code | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e4d47a72adf787f5d560374e1c44743004d25f9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946698"
---
# <a name="providing-automation-for-code"></a>Bereitstellen von Automatisierung für Code
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Erstellen eines Automatisierungsmodells für Ihren Code ist nicht erforderlich. Das SDK-Umgebung bietet kein Beispiel dafür. Einblicke in Codemodelle, finden Sie unter den <xref:EnvDTE.CodeModel> Objekt.  
  
 Um ein Codemodell zu implementieren, müssen Sie alle Schnittstellen implementieren, die von der internen Datenstruktur bestimmt werden. Die Objekte aus abgeleitet werden die `IDispatch` Klasse.  
  
 Die Objekte, die Sie erweitern, <xref:EnvDTE.CodeModel> und <xref:EnvDTE.FileCodeModel>, stehen über die <xref:EnvDTE.Project> Objekt aus, und wie folgt aussehen:  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 Sie können festlegen, ob die Implementierung nur die `CodeModel` oder `FileCodeModel` -Schnittstelle in das Objekt, das Sie zurückgeben Ihrer `Project` und <xref:EnvDTE.ProjectItem> Objekte. Geben Sie alle Funktionen von dieser Schnittstelle, die für Ihr Projektsystem geeignet ist.  
  
 Wenn Sie Funktionen wie Methoden oder Eigenschaften hinzufügen möchten, nicht die verfügbar sind aus dem Standard `CodeModel` und `FileCodeModel` Schnittstellen, erstellen Sie Ihre eigene Schnittstelle, die von der Standard erbt. Achten Sie darauf, dass Sie mit Ihrem Projektsystem zu dokumentieren, und Endbenutzer vertraut sind, sucht. Sie die Standardschnittstelle zurückgeben, aber der Benutzer kann das Aufrufen der `QueryInterface` Methode oder der Umwandlung in Ihre-Schnittstelle, wenn es bekannt ist, vorhanden sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über das Automatisierungsmodell](../../extensibility/internals/automation-model-overview.md)
