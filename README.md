def merge_sort(arr):
    if len(arr) <= 1:
        return arr  # Basis rekursi, array dengan satu elemen sudah terurut
    
    mid = len(arr) // 2
    left_half = merge_sort(arr[:mid])  # Rekursi pada bagian kiri
    right_half = merge_sort(arr[mid:])  # Rekursi pada bagian kanan

    return merge(left_half, right_half)  # Gabungkan hasil pengurutan

def merge(left, right):
    result = []
    i = j = 0

    # Gabungkan elemen dari dua array terurut
    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1

    # Tambahkan sisa elemen jika ada
    result.extend(left[i:])
    result.extend(right[j:])
    return result

# Main Program:
arr = [65, 23, 81, 43, 92, 39, 57, 16, 75]
print("Array sebelum diurutkan:", arr)

arr = merge_sort(arr)  # Panggil merge_sort

print("Array setelah diurutkan:", arr)
