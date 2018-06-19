---
ms.topic: include
ms.openlocfilehash: 502bd8d206b43fc219c850ab870db35e6c3af1c0
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2018
ms.locfileid: "32031209"
---
## <a name="sign-in-to-azure"></a>Melden Sie sich bei Azure an.
Sie müssen sich bei Azure anmelden, damit Sie Ihre Entwicklungsumgebung erstellen können. Geben Sie den folgenden Befehl in einem Terminalfenster ein:
```cmd
az login
```

> [!Note]
> Wenn Sie nicht über ein Azure-Abonnement verfügen, können Sie ein [kostenloses Konto](https://azure.microsoft.com/free) erstellen.

### <a name="if-you-have-multiple-azure-subscriptions"></a>Wenn Sie über mehrere Azure-Abonnements verfügen...
Sie können Ihre Abonnements anzeigen, indem Sie Folgendes ausführen: 
```cmd
az account list
```
Suchen Sie das Abonnement, das `isDefault: true` in der JSON-Ausgabe enthält.
Wenn dies nicht das Abonnement ist, das Sie verwenden möchten, können Sie Ihr Standard-Abonnement folgendermaßen ändern:
```cmd
az account set --subscription <subscription ID>
```
