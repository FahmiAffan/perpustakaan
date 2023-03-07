<template>
  <div>
    <navbar-component></navbar-component>
    <div class="content-wrapper">
      <div class="content-header">
        <div class="container-fluid">
          <div class="row mb-2">
            <div class="col-sm-6">
              <h1 class="m-0">Data Buku</h1>
            </div>
          </div>
        </div>
      </div>

      <div class="content">
        <div class="container-fluid">
          <div class="row">
            <div class="col-md-10">
              <div class="card card-primary card-outline">
                <div class="card-body">
                  <router-link class="btn btn-info mb-2" to="">
                    <i class="fas fa-plus"></i> Tambah
                  </router-link>
                  <table class="table table-bordered">
                    <thead>
                      <tr>
                        <th style="width: 10px">#</th>
                        <th>Judul</th>
                        <th>Pengarang</th>
                        <th>Aksi</th>
                      </tr>
                    </thead>
                    <tbody>
                      <tr v-for="(b, index) in buku" :key="index">
                        <td>{{ index + 1 }}</td>
                        <td>{{ b.nama_buku }}</td>
                        <td>{{ b.pengarang }}</td>
                        <td>
                          <div class="btn-group">
                            <router-link
                              class="btn btn-success"
                              :to="{ name: 'detailbuku', params: { id: b.id } }"
                              >Detail</router-link
                            >
                            <router-link
                              class="btn btn-warning"
                              :to="{ name: 'editbuku', params: { id: b.id } }"
                              >Edit</router-link
                            >
                            <button
                              type="button"
                              @click="hapus(b.id)"
                              class="btn btn-danger"
                            >
                              Hapus
                            </button>
                          </div>
                        </td>
                      </tr>
                    </tbody>
                  </table>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';


export default {
  name: "IndexBuku",
    Sidebarta() {
    return {
      buku: {}
    };
  },
  mounted(){
    axios
      .get("http://127.0.0.1:8000/api/data-buku")
      .then((response) => (this.buku = response.data));
  }
};
</script>
