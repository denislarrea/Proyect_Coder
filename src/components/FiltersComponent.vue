<script>
export default {
  filters: {
    toPrice(price) {
      return " U$d " + price.toFixed(2);
    },
  },
};
</script>
