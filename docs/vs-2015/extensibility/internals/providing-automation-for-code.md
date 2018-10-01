---
title: Bereitstellen von Automatisierung für Code | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 456927337331c15b3392b03175d83f2a63f87e77
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508982"
---
# <a name="providing-automation-for-code"></a>Bereitstellen von Automatisierung für Code
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Bereitstellen von Automatisierung für Code](https://docs.microsoft.com/visualstudio/extensibility/internals/providing-automation-for-code).  
  
Erstellen eines Automatisierungsmodells für Ihren Code ist nicht erforderlich. Das SDK-Umgebung bietet kein Beispiel dafür. Einblicke in Codemodelle, finden Sie unter den <xref:EnvDTE.CodeModel> Objekt.  
  
 Um ein Codemodell zu implementieren, müssen Sie alle Schnittstellen implementieren, die von der internen Datenstruktur bestimmt werden. Die Objekte aus abgeleitet werden die `IDispatch` Klasse.  
  
 Die Objekte, die Sie erweitern, <xref:EnvDTE.CodeModel> und <xref:EnvDTE.FileCodeModel>, stehen über die <xref:EnvDTE.Project> Objekt aus, und wie folgt aussehen:  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 Sie können festlegen, ob die Implementierung nur die `CodeModel` oder `FileCodeModel` -Schnittstelle in das Objekt, das Sie zurückgeben Ihrer `Project` und <xref:EnvDTE.ProjectItem> Objekte. Geben Sie alle Funktionen von dieser Schnittstelle, die für Ihr Projektsystem geeignet ist.  
  
 Wenn Sie Funktionen wie Methoden oder Eigenschaften hinzufügen möchten, nicht die verfügbar sind aus dem Standard `CodeModel` und `FileCodeModel` Schnittstellen, erstellen Sie Ihre eigene Schnittstelle, die von der Standard erbt. Achten Sie darauf, dass Sie mit Ihrem Projektsystem zu dokumentieren, und Endbenutzer vertraut sind, sucht. Sie die Standardschnittstelle zurückgeben, aber der Benutzer kann das Aufrufen der `QueryInterface` Methode oder der Umwandlung in Ihre-Schnittstelle, wenn es bekannt ist, vorhanden sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über das Automatisierungsmodell](../../extensibility/internals/automation-model-overview.md)

