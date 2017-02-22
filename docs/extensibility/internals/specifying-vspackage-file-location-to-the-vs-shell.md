---
title: "Angabe des VSPackage Dateispeicherorts f&#252;r die VS-Shell | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "verwaltete VSPackages, Dateispeicherort"
  - "VSPackages, verwaltete Dateispeicherort"
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Angabe des VSPackage Dateispeicherorts f&#252;r die VS-Shell
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] muss zum Suchen der Assembly\-DLL zum Laden von VSPackages können. Sie können ihn auf verschiedene Weise finden, wie in der folgenden Tabelle beschrieben.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|Verwenden Sie den Registrierungsschlüssel Codebasis.|Die Codebasis Schlüssel verwendet werden kann, um direkte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zum Laden der VSPackage\-Assembly über einen vollqualifizierten Pfad. Der Wert des Schlüssels muss der Pfad zur DLL. Dies ist die beste Möglichkeit, haben [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die Paket\-Assembly zu laden. Diese Technik wird manchmal als die "CodeBase privatem Installation Directory Technik." bezeichnet Während der Registrierung der Wert der Codebasis wird an übergeben Attributklassen Registrierung durch eine Instanz von der <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> Typ.|  
|Legen Sie die DLL in das **PrivateAssemblies** Verzeichnis.|Fügen Sie die Assembly in der **PrivateAssemblies** \-Unterverzeichnis der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Verzeichnis. Assemblys im Verzeichnis **PrivateAssemblies** werden automatisch erkannt, jedoch sind nicht sichtbar, in der **Verweise hinzufügen** \(Dialogfeld\). Der Unterschied zwischen **PrivateAssemblies** und **PublicAssemblies** ist, die Assemblys in **PublicAssemblies** werden aufgelistet, der **Verweise hinzufügen** \(Dialogfeld\). Wenn Sie möchten, dass Sie nicht "CodeBase privatem Installationsverzeichnis" Technik verwenden, installieren Sie in der **PrivateAssemblies** Verzeichnis.|  
|Verwenden Sie eine Assembly mit starkem Namen und den Registrierungsschlüssel für die Assembly.|Die Assembly\-Schlüssel verwendet werden kann, um explizit zu leiten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ein starkes Laden mit dem Namen VSPackage\-Assembly. Der Wert des Schlüssels sollte der starke Name der Assembly.|  
|Legen Sie die DLL in das **PublicAssemblies** Verzeichnis.|Schließlich die Assembly kann auch platziert werden in der **PublicAssemblies** Unterverzeichnis. Assemblys im Verzeichnis **PublicAssemblies** werden automatisch erkannt, und werden auch der **Verweise hinzufügen** im Dialogfeld [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].<br /><br /> VSPackage\-Assemblys sollten nur angeordnet werden, der **PublicAssemblies** Verzeichnis enthalten verwalteten Komponenten, die von anderen Entwicklern VSPackage wiederverwendet werden sollen. Der Großteil der Assemblys dieses Kriterium nicht erfüllen.|  
  
> [!NOTE]
>  Verwenden Sie für alle abhängigen Assemblys mit starkem Namen, signierte Assemblys. Diese Assemblys sollte auch in Ihrem eigenen Verzeichnis oder dem globalen Assemblycache \(GAC\) installiert werden. Dies schützt vor Konflikte mit Assemblys, die denselben Dateinamen, als schwachen Namen Bindung bezeichnet.