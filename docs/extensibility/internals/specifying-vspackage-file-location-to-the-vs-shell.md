---
title: Angeben des VSPackage-Dateispeicherorts für die VS-Shell | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f112da4e79bff06d12472f0af7a3fe47b2f25da4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704976"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Angeben des VSPackage-Dateispeicherorts für die VS Shell
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]muss in der Lage sein, die Baugruppen-DLL zu finden, um das VSPackage zu laden. Sie können es auf verschiedene Weise finden, wie in der folgenden Tabelle beschrieben.

| Methode | BESCHREIBUNG |
| - | - |
| Verwenden Sie den CodeBase-Registrierungsschlüssel. | Der CodeBase-Schlüssel kann [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verwendet werden, um die VSPackage-Assembly aus einem vollqualifizierten Dateipfad zu laden. Der Wert des Schlüssels sollte der Dateipfad zur DLL sein. Dies ist der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] beste Weg, um Ihre Paketassembly zu laden. Diese Technik wird manchmal als "CodeBase/private Installationsverzeichnistechnik" bezeichnet. Während der Registrierung wird der Wert der Codebasis über eine <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> Instanz des Typs an die Registrierungsattributklassen übergeben. |
| Platzieren Sie die DLL im **PrivateAssemblies-Verzeichnis.** | Platzieren Sie die Assembly im **Unterverzeichnis PrivateAssemblies** des [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Verzeichnisses. Assemblys, die sich in **PrivateAssemblies** befinden, werden automatisch erkannt, sind aber im Dialogfeld **Referenzen** hinzufügen nicht sichtbar. Der Unterschied zwischen **PrivateAssemblies** und **PublicAssemblies** besteht darin, dass Assemblys in **PublicAssemblies** im Dialogfeld **Referenzen hinzufügen** aufgelistet werden. Wenn Sie die Technik "CodeBase/privates Installationsverzeichnis" nicht verwenden möchten, sollten Sie die Installation im **PrivateAssemblies-Verzeichnis** durchführen. |
| Verwenden Sie eine Assembly mit starkem Namen und den Assemblyregistrierungsschlüssel. | Der Assemblyschlüssel kann verwendet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] werden, um explizit zum Laden einer starken VSPackage-Assembly zu leiten. Der Wert des Schlüssels sollte der starke Name der Assembly sein. |
| Platzieren Sie die DLL im **PublicAssemblies-Verzeichnis.** | Schließlich kann die Assembly auch im **Unterverzeichnis PublicAssemblies** abgelegt werden. Assemblys in **PublicAssemblies** werden automatisch erkannt und **Add References** werden auch [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]im Dialogfeld Referenzen hinzufügen in angezeigt.<br /><br /> VSPackage-Assemblys sollten nur dann im **PublicAssemblies-Verzeichnis** platziert werden, wenn sie verwaltete Komponenten enthalten, die von anderen VSPackage-Entwicklern wiederverwendet werden sollen. Die Mehrheit der Versammlungen erfüllt dieses Kriterium nicht. |

> [!NOTE]
> Verwenden Sie stark benannte, signierte Assemblys für alle abhängigen Assemblys. Diese Assemblys sollten auch in Ihrem eigenen Verzeichnis oder im globalen Assemblycache (GAC) installiert werden. Dies schützt vor Konflikten mit Assemblys mit demselben Basisdateinamen, der als "Schwachname-Bindung" bezeichnet wird.
