---
title: 'Vorgehensweise: Erstellen eines lokalisierten Bootstrapperpakets | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- localized bootstrapper packages
- dependencies, creating localized bootstrapper packages
- prerequisites, creating localized bootstrapper packages
ms.assetid: 66a1bc7e-6540-4164-963d-557196a69d8a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1083633410c42c63f8c3e9a2ff341a2278f0b63a
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153214"
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>Gewusst wie: Erstellen eines lokalisierten Bootstrapperpakets
Nachdem Sie ein Bootstrapperpaket erstellt haben, können Sie lokalisierte Versionen des Bootstrapperpakets erstellen, indem Sie mindestens zwei Dateien für jedes Gebietsschema erstellen: eine Software-Lizenzbedingungen Datei (z. B. eine *eula.rtf*) und ein Paketmanifest (*"Package.xml"*).  
  
 Visual Studio 2010 umfasst standardmäßig nur lokalisierte Bootstrapperpakete für .NET Framework 4, .NET Framework 4 Client Profile, F# Runtime 2.0 und F# Runtime 4.0. Mit den folgenden drei Schritten können Sie lokalisierte Pakete für andere Bootstrapper erstellen.  
  
1.  Erstellen Sie einen Ordner mit dem Namen des Gebietsschemas unter *\Programme\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\\<Bootstrapperpaketname >*.  
  
2.  Erstellen Sie eine Datei, die die Softwarelizenzbedingungen für das Bootstrapperpaket enthält, und legen Sie diese in dem neuen Ordner ab.  
  
3.  Erstellen Sie ein Paketmanifest mit dem Namen *"Package.xml"*, aktualisieren Sie die Zeichenfolgen und die Kultur, und legen Sie die Datei in den neuen Ordner. Wenn Sie bereits ein Bootstrapperpaket von Visual Studio in der Zielsprache erstellt haben, können Sie die Visual Studio kopieren *"Package.xml"* Datei, und es in diesem Schritt ändern.  
  
> [!NOTE]
>  Wenn Sie ein Setup-Projekt zum Bereitstellen von Anwendungen verwenden, können Sie Ihre Anwendung lokalisieren, indem Sie ändern die **Lokalisierung** Eigenschaft.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-create-a-localized-bootstrapper-package"></a>So erstellen Sie ein lokalisiertes Bootstrapperpaket  
  
1.  Erstellen Sie einen Ordner mit dem Namen des Gebietsschemas.  
  
     Erstellen Sie auf 32-Bit-Computern den Ordner, in der *\Programme\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\\<Bootstrapperpaketname >\\*  Ordner.  
  
     Erstellen Sie auf 64-Bit-Computern den Ordner, in der *\Program Files (x 86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\\<Bootstrapperpaketname >\\*  Ordner.  
  
     In der folgenden Tabelle sind die Ordnernamen dargestellt, die Sie für die Übereinstimmung mit einem Gebietsschema verwenden können.  
  
    |Gebietsschema|Ordnername|  
    |------------|-----------------|  
    |Chinesisch (vereinfacht)|zh-Hans|  
    |Chinesisch (traditionell)|zh-Hant|  
    |Tschechisch|cs|  
    |Deutsch|de|  
    |Englisch|en|  
    |Spanisch|es|  
    |Französisch|fr|  
    |Italienisch|it|  
    |Koreanisch|ko|  
    |Japanisch|ja|  
    |Polnisch|pl|  
    |Portugiesisch (Brasilien)|pt-BR|  
    |Russisch|ru|  
    |Türkisch|tr|  
  
2.  Erstellen Sie eine Datei, die die Softwarelizenzbedingungen für das Bootstrapperpaket enthält, und legen Sie diese in dem neuen Ordner ab.  
  
3.  Erstellen Sie ein Paketmanifest mit dem Namen *"Package.xml"* und fügen Sie ihn in den neuen Ordner. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen eines Paketmanifests](../deployment/how-to-create-a-package-manifest.md).  
  
4.  Aktualisieren Sie den Abschnitt `<Strings>` des Paketmanifests so, dass die Zeichenfolgen die korrekte Sprache für das Gebietsschema aufweisen.  
  
5.  Ändern Sie den Wert `<String Name="Culture">` so, dass er mit dem Ordnernamen übereinstimmt.  
  
6.  Speichern Sie die *"Package.xml"* Datei.  
  
### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>So erstellen Sie ein Bootstrapperpaket für .NET Framework 3.5 Service Pack 1 lokalisiert in Französisch  
  
1.  Erstellen Sie einen Ordner mit dem Namen *"fr"*. Der Ordnername muss mit dem Gebietsschemanamen übereinstimmen.  
  
     Erstellen Sie auf 32-Bit-Computern den Ordner, in der *\Programme\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\\*  Ordner.  
  
     Erstellen Sie auf 64-Bit-Computern den Ordner, in der *\Program Files (x 86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\\*  Ordner.  
  
2.  Legen Sie eine lokalisierte Version der Software-Lizenzbedingungen in der *"fr"* Ordner.  
  
3.  Kopieren der *\Programme Dateien (x86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\en\package.xml* -Datei in die *"fr"* Ordner, und öffnen Sie die Datei im XML-Designer.  
  
4.  Aktualisieren Sie den Abschnitt `<Strings>` des Paketmanifests so, dass die Fehlerzeichenfolgen auf Französisch sind.  
  
5.  Ändern der `<String Name="Culture">` Wert *"fr"*.  
  
6.  Speichern Sie die *"Package.xml"* Datei.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Bootstrapperpaketen](../deployment/creating-bootstrapper-packages.md)   
 [Vorbedingungen für die anwendungsbereitstellung](../deployment/application-deployment-prerequisites.md)   
 [Gewusst wie: Erstellen eines Paketmanifests](../deployment/how-to-create-a-package-manifest.md)