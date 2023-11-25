db.collection.aggregate([
  {"$match": {
              "composicao":"ferro"
             }
  },
  {"$group":
    {
      "_id": "$vendedor",
      "soma_total": {
                      "$sum": 1
                    }
    }
  }
])
