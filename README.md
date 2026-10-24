# Hashing-method
Hashing – Employee ID Storage

# Hash function
def hash_fn(key, size):
    return key % size


# Open Addressing – Linear Probing
def open_addressing(ids, size):
    table = [None] * size

    print("\nOpen Addressing (Linear Probing):")

    for emp_id in ids:
        idx = hash_fn(emp_id, size)
        original = idx

        while table[idx] is not None:
            idx = (idx + 1) % size

            if idx == original:
                print(f"Table full! Cannot insert {emp_id}")
                break

        else:
            table[idx] = emp_id
            print(
                f"Inserted {emp_id} at index {idx} "
                f"(hash={original})"
            )

    print("Hash Table:", table)


# Separate Chaining – Closed Addressing
def separate_chaining(ids, size):
    table = [[] for _ in range(size)]

    print("\nSeparate Chaining (Closed Addressing):")

    for emp_id in ids:
        idx = hash_fn(emp_id, size)
        table[idx].append(emp_id)

        print(f"Inserted {emp_id} at index {idx}")

    print("Hash Table:")

    for i, chain in enumerate(table):
        if chain:
            print(f"  [{i}] -> {chain}")


# Main Program
employee_ids = [1001, 1123, 1198, 1455, 1677]
table_size = 10

print("Employee IDs:", employee_ids)
print("Table Size:", table_size)

open_addressing(employee_ids, table_size)
separate_chaining(employee_ids, table_size)