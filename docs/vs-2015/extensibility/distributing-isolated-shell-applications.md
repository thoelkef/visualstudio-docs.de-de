---
title: Verteilen von Isolated Shell-Anwendungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d05e6a88c9da52492a49462880a04e578feadb5c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49305811"
---
# <a name="distributing-isolated-shell-applications"></a>Verteilen von Isolated Shell-Anwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie müssen Visual Studio und Visual Studio SDK installieren, um eine isolierte Shell-Anwendung zu erstellen. Um die Anwendung auf die Computer anderer Benutzer oder Kunden zu verteilen, müssen Sie spezielles verteilbares Paket für die isolated Shell einschließen.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>Voraussetzungen für das Verteilen von Isolated Shell-Anwendungen  
  
|name|Beschreibung|  
|----------|-----------------|  
|Visual Studio SDK|Das SDK benötigen Sie zum Entwickeln und testen die Erweiterungen der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Sie können auch das SDK verwenden, um Ihre eigene Instanz von Visual Studio isolierte Shell zu erstellen.<br /><br /> Visual Studio ist eine Voraussetzung für das SDK.|  
|Microsoft Visual Studio isolierte Shell Redistributable|Die Redistributable-Komponente, dass Sie in Ihrem Setup-Programm einschließen, bei der Erstellung einer Umgebung Tools für Visual Studio isolierte Shell. Das isolierte Shell redistributable Package enthält die .NET Framework 4.5.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>Erstellen ein Installationsprogramm für die Anwendung  
 Sie müssen eine spezielle Installationsprogramm für die integrierte oder isolierte Shell-Anwendung erstellen. Weitere Informationen finden Sie unter [Installieren einer Isolated Shell-Anwendung](../extensibility/installing-an-isolated-shell-application.md).  
  
## <a name="allowing-for-updates-to-your-application"></a>Updates für Ihre Anwendung zulassen  
 Ihr Installationsprogramm muss die Möglichkeit, dass die Anwendung, entweder durch Microsoft-Updates oder Updates für Ihr Unternehmen aktualisiert werden ermöglichen. Weitere Informationen zu Updates finden Sie unter [Wartung von Richtlinien für die isolierte Shell-Anwendungen](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).

