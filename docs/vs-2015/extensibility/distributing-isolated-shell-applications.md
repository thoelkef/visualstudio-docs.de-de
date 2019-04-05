---
title: Verteilen von Isolated Shell-Anwendungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bf0d8a4cab8d30a56e84d1a6869c2c842b982aea
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961258"
---
# <a name="distributing-isolated-shell-applications"></a>Verteilen von Isolated Shell-Anwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie müssen Visual Studio und Visual Studio SDK installieren, um eine isolierte Shell-Anwendung zu erstellen. Um die Anwendung auf die Computer anderer Benutzer oder Kunden zu verteilen, müssen Sie spezielles verteilbares Paket für die isolated Shell einschließen.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>Voraussetzungen für das Verteilen von Isolated Shell-Anwendungen  
  
|Name|Beschreibung|  
|----------|-----------------|  
|Visual Studio SDK|Das SDK benötigen Sie zum Entwickeln und testen die Erweiterungen der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Sie können auch das SDK verwenden, um Ihre eigene Instanz von Visual Studio isolierte Shell zu erstellen.<br /><br /> Visual Studio ist eine Voraussetzung für das SDK.|  
|Microsoft Visual Studio isolierte Shell Redistributable|Die Redistributable-Komponente, dass Sie in Ihrem Setup-Programm einschließen, bei der Erstellung einer Umgebung Tools für Visual Studio isolierte Shell. Das isolierte Shell redistributable Package enthält die .NET Framework 4.5.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>Erstellen ein Installationsprogramm für die Anwendung  
 Sie müssen eine spezielle Installationsprogramm für die integrierte oder isolierte Shell-Anwendung erstellen. Weitere Informationen finden Sie unter [Installieren einer Isolated Shell-Anwendung](../extensibility/installing-an-isolated-shell-application.md).  
  
## <a name="allowing-for-updates-to-your-application"></a>Updates für Ihre Anwendung zulassen  
 Ihr Installationsprogramm muss die Möglichkeit, dass die Anwendung, entweder durch Microsoft-Updates oder Updates für Ihr Unternehmen aktualisiert werden ermöglichen. Weitere Informationen zu Updates finden Sie unter [Wartung von Richtlinien für die isolierte Shell-Anwendungen](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).
