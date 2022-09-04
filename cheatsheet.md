# Entity Framework Core - Cheat sheet
We all know EF. We all know the limitations and benefits of the ORM. Most conversations, center are around the two different scenarios to use EF Core.

1) **Connected scenarios**. Often used in batch or sequential applications.
2) **Disconnected scenarios**. Often used in APIs or async applications.

| Area | Cheat | Connected | Disconnected |
| - | - | - | - |
| Update | Methods of update | Get the entity from dbContext (as tracking), then map the updates properties and call SaveChanges(). | Call Attach() or Update() or Set().Entity(obj).State<sub>1</sub> |
| Update | Impact of update | Only columns<sub>2</sub> that are changed, removing items of collections are removed. | All properties<sub>2</sub> are updated, removed items of collections must be deleted using .Remove() |

### Cheats

### Sub notes
1) There are many strategies for marking an entity ready for update.
2) There is no performance benefit of few vs. many column updates if database i SQL server. Data is written as 8kb per write, and columns require reorder anyhow.
