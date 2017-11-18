---
redirect_url: shell/distributing-isolated-shell-applications
title: Verteilen von Isolated Shell-Anwendungen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a40d2b8c108d7180ffc68ac2eee6811d49b21c08
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="distributing-isolated-shell-applications"></a>Verteilen von Isolated Shell-Anwendungen
Sie müssen Visual Studio und Visual Studio SDK installieren, um eine isolierte Shell-Anwendung zu erstellen. Um die Anwendung mit den Computern anderer Benutzer oder Kunden zu verteilen, müssen Sie besonderes verteilbares Paket für die isolierte Shell einschließen.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>Voraussetzungen für das Verteilen von Isolated Shell-Anwendungen  
  
|Name|Beschreibung|  
|----------|-----------------|  
|Visual Studio SDK|Das SDK benötigen Sie zum Entwickeln und Testen von Erweiterungen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Das SDK können auch eine eigene Instanz des Visual Studio isolated Shell erstellen.<br /><br /> Visual Studio ist eine Voraussetzung für das SDK.|  
|Microsoft Visual Studio isolierte Shell Redistributable|Das verteilbare Paket, dass Sie im Setup-Programm enthalten, bei der Erstellung einer Umgebung Tools im Visual Studio isolierte Shell. Das verteilbare Paket von isolierte Shell schließt .NET Framework 4.5.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>Erstellen ein Installationsprogramm für die Anwendung  
 Sie müssen eine spezielle Installationsprogramm für die integrierte oder isolierte Shell-Anwendung erstellen. Weitere Informationen finden Sie unter [Installieren einer isolierten Shell-Anwendung](../extensibility/installing-an-isolated-shell-application.md).  
  
## <a name="allowing-for-updates-to-your-application"></a>Updates für Ihre Anwendung zulassen  
 Das Installationsprogramm muss die Möglichkeit, dass die Anwendung, von Microsoft-Updates oder Ihres Unternehmens Updates aktualisiert werden zulassen. Weitere Informationen zu Updates finden Sie unter [Wartung Richtlinien für isolierte Shell-Anwendungen](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).