<template>
    <div class="page row">
    <div class="col-md-10">
    <InputSearch v-model="searchText" />
    </div>
    <div class="mt-3 col-md-6">
    <h4>
    Danh bạ
    <i class="fas fa-address-book"></i>
    </h4>
    <ContactList
    v-if="filteredContactsCount > 0"
    :contacts="filteredContacts"
    v-model:activeIndex="activeIndex"
    />
    <p v-else>Không có liên hệ nào.</p>
    <div class="mt-3 row justify-content-around align-items-center">
    <button class="btn btn-sm btn-primary" @click="refreshList()">
    <i class="fas fa-redo"></i> Làm mới
    </button>
    <button class="btn btn-sm btn-success" @click="goToAddContact">
    <i class="fas fa-plus"></i> Thêm mới
    </button>
    

    <button
    class="btn btn-sm btn-danger"
    @click="removeAllContacts"
    >
    <i class="fas fa-trash"></i> Xóa tất cả
    </button>
    </div>
    </div>
    <div class="mt-3 col-md-6">
    <div v-if="activeContact">
    <h4>
    Chi tiết Liên hệ
    <i class="fas fa-address-card"></i>
    </h4>
    <ContactCard :contact="activeContact" />
    </div>
    </div>
    </div>
    </template>
    <script>
    import ContactCard from "@/components/ContactCard.vue";
    import InputSearch from "@/components/InputSearch.vue";
    import ContactList from "@/components/ContactList.vue";
    import ContactService from "@/services/contact.service";
    export default {
    components: {
    ContactCard,
    InputSearch,
    ContactList,
    },
    // Đoạn mã xử lý đầy đủ sẽ trình bày bên dưới
    };
    </script>
    <style scoped>
    .page {
    text-align: left;
    max-width: 750px;
    }
    </style>