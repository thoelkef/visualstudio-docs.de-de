---
title: "Angeben der VSPackage-Dateispeicherort für die Visual Studio-Shell | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 35bd935683f8ace47536389ebc65f34311e9fcfd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Angeben der VSPackage-Dateispeicherort für die Visual Studio-Shell
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]muss zum Suchen der Assembly-DLL für das VSPackage lädt, können. Sie können ihn auf verschiedene Weise finden, wie in der folgenden Tabelle beschrieben.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|Verwenden Sie den Registrierungsschlüssel "CodeBase".|Der Codebasis Schlüssel dienen zum leiten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zum Laden der VSPackage-Assembly über einen vollqualifizierten Pfad. Der Wert des Schlüssels sollte der Dateipfad für die DLL. Dies ist die beste Möglichkeit, haben [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die Paket-Assembly zu laden. Diese Technik wird manchmal als die "CodeBase und privatem Installation Directory Technik." bezeichnet Während der Registrierung der Wert der Codebasis übergeben an der Registrierung Attributklassen über eine Instanz der <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> Typ.|  
|Platzieren Sie die DLL in den **PrivateAssemblies** Verzeichnis.|Platzieren Sie die Assembly in die **PrivateAssemblies** Unterverzeichnis der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Verzeichnis. Assemblys im Verzeichnis **PrivateAssemblies** werden automatisch erkannt, jedoch sind nicht sichtbar, in der **Verweise hinzufügen** (Dialogfeld). Der Unterschied zwischen **PrivateAssemblies** und **PublicAssemblies** ist, die Assemblys in **PublicAssemblies** aufgelistet sind, der **Verweise hinzufügen**  (Dialogfeld). Wenn Sie haben nicht das Verfahren "Installationsverzeichnis CodeBase/Private" verwenden, installieren Sie in der **PrivateAssemblies** Verzeichnis.|  
|Verwenden Sie eine Assembly mit starkem Namen und den Registrierungsschlüssel für die Assembly.|Der Schlüssel der Assembly genutzt werden, leiten explizit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ein sicheres Laden mit dem Namen VSPackage-Assembly. Der Wert des Schlüssels sollte der starke Name der Assembly sein.|  
|Platzieren Sie die DLL in den **PublicAssemblies** Verzeichnis.|Schließlich die Assembly kann auch platziert werden in der **PublicAssemblies** Unterverzeichnis. Assemblys im Verzeichnis **PublicAssemblies** werden automatisch erkannt und wird auch angezeigt, der **Verweise hinzufügen** im Dialogfeld [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].<br /><br /> VSPackage-Assemblys sollten nur platziert werden, der **PublicAssemblies** Verzeichnis enthalten verwalteten Komponenten, die von anderen Entwicklern VSPackage wiederverwendet werden sollen. Die meisten Assemblys dieses Kriterium nicht erfüllen.|  
  
> [!NOTE]
>  Verwenden Sie für alle abhängigen Assemblys mit starkem Namen, signierte Assemblys. Diese Assemblys sollte auch in Ihrem eigenen Verzeichnis oder im globalen Assemblycache (GAC) installiert werden. Dies schützt vor steht in Konflikt mit Assemblys, die Basisdatei gleichnamigen, als schwachen Namen Bindung bezeichnet.