---
title: Recursos de serviço geridos
description: Os serviços geridos são serviços aos quais um parceiro delegou privilégios administrativos. Os parceiros podem fornecer apoio e pedidos de serviço de arquivo em nome dos seus serviços geridos.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 582efe75fd18a9174dd5dc173c290bee25443ee9
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548129"
---
# <a name="managed-service-resources"></a><span data-ttu-id="956f9-104">Recursos de serviço geridos</span><span class="sxs-lookup"><span data-stu-id="956f9-104">Managed service resources</span></span>

<span data-ttu-id="956f9-105">**Aplica-se a**: Partner Center | Partner Center operado pela 21Vianet | Centro de Parceiros para | Microsoft Cloud Germany Centro de Parceiros para Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="956f9-105">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="956f9-106">Os serviços geridos são serviços aos quais um parceiro delegou privilégios administrativos.</span><span class="sxs-lookup"><span data-stu-id="956f9-106">Managed services are services to which a partner has delegated admin privileges.</span></span> <span data-ttu-id="956f9-107">Os parceiros podem fornecer apoio e pedidos de serviço de arquivo em nome dos seus serviços geridos.</span><span class="sxs-lookup"><span data-stu-id="956f9-107">Partners can provide support for and file service requests on the behalf of their managed services.</span></span>

## <a name="managedservice"></a><span data-ttu-id="956f9-108">Serviço Gerido</span><span class="sxs-lookup"><span data-stu-id="956f9-108">ManagedService</span></span>

<span data-ttu-id="956f9-109">Descreve um serviço gerido.</span><span class="sxs-lookup"><span data-stu-id="956f9-109">Describes a managed service.</span></span>

| <span data-ttu-id="956f9-110">Propriedade</span><span class="sxs-lookup"><span data-stu-id="956f9-110">Property</span></span>   | <span data-ttu-id="956f9-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="956f9-111">Type</span></span>                | <span data-ttu-id="956f9-112">Description</span><span class="sxs-lookup"><span data-stu-id="956f9-112">Description</span></span>                                              |
|------------|---------------------|----------------------------------------------------------|
| <span data-ttu-id="956f9-113">Id</span><span class="sxs-lookup"><span data-stu-id="956f9-113">Id</span></span>         | <span data-ttu-id="956f9-114">string</span><span class="sxs-lookup"><span data-stu-id="956f9-114">string</span></span>              | <span data-ttu-id="956f9-115">A identificação de serviço gerido.</span><span class="sxs-lookup"><span data-stu-id="956f9-115">The managed service ID.</span></span>                                  |
| <span data-ttu-id="956f9-116">Name</span><span class="sxs-lookup"><span data-stu-id="956f9-116">Name</span></span>       | <span data-ttu-id="956f9-117">string</span><span class="sxs-lookup"><span data-stu-id="956f9-117">string</span></span>              | <span data-ttu-id="956f9-118">O nome do serviço gerido.</span><span class="sxs-lookup"><span data-stu-id="956f9-118">The name of the managed service.</span></span>                         |
| <span data-ttu-id="956f9-119">Nome do Grupo</span><span class="sxs-lookup"><span data-stu-id="956f9-119">GroupName</span></span>  | <span data-ttu-id="956f9-120">string</span><span class="sxs-lookup"><span data-stu-id="956f9-120">string</span></span>              | <span data-ttu-id="956f9-121">O nome do grupo a que pertence o serviço.</span><span class="sxs-lookup"><span data-stu-id="956f9-121">The name of the group to which the service belongs.</span></span>      |
| <span data-ttu-id="956f9-122">Ligações</span><span class="sxs-lookup"><span data-stu-id="956f9-122">Links</span></span>      | <span data-ttu-id="956f9-123">ManagedServiceLinks</span><span class="sxs-lookup"><span data-stu-id="956f9-123">ManagedServiceLinks</span></span> | <span data-ttu-id="956f9-124">As ligações de recursos correspondentes ao serviço gerido.</span><span class="sxs-lookup"><span data-stu-id="956f9-124">The resource links corresponding to the managed service.</span></span> |
| <span data-ttu-id="956f9-125">Atributos</span><span class="sxs-lookup"><span data-stu-id="956f9-125">Attributes</span></span> | <span data-ttu-id="956f9-126">RecursosTributos</span><span class="sxs-lookup"><span data-stu-id="956f9-126">ResourceAttributes</span></span>  | <span data-ttu-id="956f9-127">Os metadados atribuem correspondentes ao acordo.</span><span class="sxs-lookup"><span data-stu-id="956f9-127">The metadata attributes corresponding to the agreement.</span></span>  |

## <a name="managedservicelinks"></a><span data-ttu-id="956f9-128">ManagedServiceLinks</span><span class="sxs-lookup"><span data-stu-id="956f9-128">ManagedServiceLinks</span></span>

<span data-ttu-id="956f9-129">Contém os links que permitem ao parceiro com permissões de administração delegadas fornecer suporte para o serviço.</span><span class="sxs-lookup"><span data-stu-id="956f9-129">Contains the links that allow the partner with delegated admin permissions to provide support for the service.</span></span>

| <span data-ttu-id="956f9-130">Propriedade</span><span class="sxs-lookup"><span data-stu-id="956f9-130">Property</span></span>      | <span data-ttu-id="956f9-131">Tipo</span><span class="sxs-lookup"><span data-stu-id="956f9-131">Type</span></span> | <span data-ttu-id="956f9-132">Description</span><span class="sxs-lookup"><span data-stu-id="956f9-132">Description</span></span>                 |
|---------------|------|-----------------------------|
| <span data-ttu-id="956f9-133">Serviço de Administração</span><span class="sxs-lookup"><span data-stu-id="956f9-133">AdminService</span></span>  | <span data-ttu-id="956f9-134">Ligação</span><span class="sxs-lookup"><span data-stu-id="956f9-134">Link</span></span> | <span data-ttu-id="956f9-135">O serviço de administração URI.</span><span class="sxs-lookup"><span data-stu-id="956f9-135">The admin service URI.</span></span>      |
| <span data-ttu-id="956f9-136">Saúde de Serviço</span><span class="sxs-lookup"><span data-stu-id="956f9-136">ServiceHealth</span></span> | <span data-ttu-id="956f9-137">Ligação</span><span class="sxs-lookup"><span data-stu-id="956f9-137">Link</span></span> | <span data-ttu-id="956f9-138">O serviço de saúde URI.</span><span class="sxs-lookup"><span data-stu-id="956f9-138">The service health URI.</span></span>     |
| <span data-ttu-id="956f9-139">ServiceTicket</span><span class="sxs-lookup"><span data-stu-id="956f9-139">ServiceTicket</span></span> | <span data-ttu-id="956f9-140">Ligação</span><span class="sxs-lookup"><span data-stu-id="956f9-140">Link</span></span> | <span data-ttu-id="956f9-141">O bilhete de serviço URI.</span><span class="sxs-lookup"><span data-stu-id="956f9-141">The service ticket URI.</span></span>     |
| <span data-ttu-id="956f9-142">Autónomo</span><span class="sxs-lookup"><span data-stu-id="956f9-142">Self</span></span>          | <span data-ttu-id="956f9-143">Ligação</span><span class="sxs-lookup"><span data-stu-id="956f9-143">Link</span></span> | <span data-ttu-id="956f9-144">O auto-URI.</span><span class="sxs-lookup"><span data-stu-id="956f9-144">The self-URI.</span></span>               |
| <span data-ttu-id="956f9-145">Seguinte</span><span class="sxs-lookup"><span data-stu-id="956f9-145">Next</span></span>          | <span data-ttu-id="956f9-146">Ligação</span><span class="sxs-lookup"><span data-stu-id="956f9-146">Link</span></span> | <span data-ttu-id="956f9-147">A próxima página de artigos.</span><span class="sxs-lookup"><span data-stu-id="956f9-147">The next page of items.</span></span>     |
| <span data-ttu-id="956f9-148">Anterior</span><span class="sxs-lookup"><span data-stu-id="956f9-148">Previous</span></span>      | <span data-ttu-id="956f9-149">Ligação</span><span class="sxs-lookup"><span data-stu-id="956f9-149">Link</span></span> | <span data-ttu-id="956f9-150">A página anterior dos artigos.</span><span class="sxs-lookup"><span data-stu-id="956f9-150">The previous page of items.</span></span> |

