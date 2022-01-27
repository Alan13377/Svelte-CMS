<script context="module">
    import { gql, GraphQLClient } from 'graphql-request'
  
    export const load = async () => {
      const client = new GraphQLClient(
        import.meta.env.VITE_GRAPHQL_API
      )
  
      const query = gql`
        query GetProjects {
          projects {
            name
            slug
            description
            demo
            sourceCode
            image {
              url
            }
          }
        }
      `
  
      const { projects } = await client.request(query)
  
      return {
        props: {
          projects,
        },
      }
    }
  </script>
  
  <script>
    export let projects
  </script>
  
  <pre>{JSON.stringify(projects, null, 2)}</pre>