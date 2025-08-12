# 🏗️ infrastructure/repositories/ (clients domain)

?

---

## 📁 Example

```
domains/clients/infrastructure/repositories/
└── client.prisma-repository.ts
```

---

## ✅ Best practices

- ?

---

## 🧠 Example

```ts
export class PrismaClientRepository implements ClientRepository {
  async save(client: Client): Promise<void> {
    await prisma.client.create({
      data: ClientMapper.toCreatePrisma(client),
    })
  }

  async update(client: Client): Promise<void> {
    await prisma.client.update({
      where: { id: client.id },
      data: ClientMapper.toUpdatePrisma(client),
    })
  }

  async findById(id: string): Promise<Client | null> {
    const raw = await prisma.client.findUnique({ where: { id } })
    return raw ? ClientMapper.toDomain(raw) : null
  }

  async findByEmail(email: string): Promise<Client | null> {
    const raw = await prisma.client.findUnique({ where: { email } })
    return raw ? ClientMapper.toDomain(raw) : null
  }

  async findAll(query: QueryDto): Promise<ClientListResult> {
    const whereClause: Prisma.ClientWhereInput = {}

    if (query.search && query.search.trim() !== '') {
      whereClause.OR = [
        { email: { contains: query.search, mode: 'insensitive' } },
        { namz: { contains: query.search, mode: 'insensitive' } },
      ]
    }

    const rawClients = await prisma.client.findMany({
      take: query.take + 1,
      cursor: query.cursor ? { id: query.cursor } : undefined,
      where: whereClause,
      orderBy: [{ createdAt: 'desc' }],
    })

    const hasNext = rawClients.length > query.take
    const nextCursor = hasNext ? rawClients[rawClients.length - 1].id : null

    if (hasNext) rawClients.pop()

    const total = await prisma.client.count({ where: whereClause })

    return {
      clients: rawClients.map(ClientMapper.toDomain),
      nextCursor,
      total,
    }
  }

  async delete(id: string): Promise<void> {
    await prisma.client.delete({ where: { id } })
  }
}
```