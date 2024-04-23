<template>
    <div>
      <h2>Daftar Kegiatan</h2>
      <table>
        <thead>
          <tr>
            <th>Nama Kegiatan</th>
            <th>Tanggal Kegiatan</th>
            <th>Status</th>
            <th>Aksi</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(activity, index) in activities" :key="index">
            <td>{{ activity.name }}</td>
            <td>{{ activity.date }}</td>
            <td>{{ activity.completed ? 'Selesai' : 'Belum Selesai' }}</td>
            <td>
              <button @click="toggleCompletion(index)">
                {{ activity.completed ? 'Batal Selesai' : 'Tandai Selesai' }}
              </button>
              <button @click="removeActivity(index)">Hapus</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      activities: {
        type: Array,
        default: () => []
      }
    },
    methods: {
      toggleCompletion(index) {
        this.$emit('toggle-completion', index);
      },
      removeActivity(index) {
        this.$emit('remove-activity', index);
      }
    }
  };
  </script>
  